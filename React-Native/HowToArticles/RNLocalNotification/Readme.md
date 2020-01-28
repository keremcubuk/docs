# React Native Local Push Notification

In react native applications notification is a hardest one to implement, but we will break this perception. In your device, notifications use native notification modules so that you should implement the configuration to your project. We will use the simpliest version of notification app.


## How to implement

Firstly, we must install two different `react-native-push-notification` library. If you ask why two packages? ios and android notification libraries seperated by [react-native-community](https://github.com/react-native-community) decision. Therefore, this packages work together but, you should implement seperately.

```shell
npm install https://github.com/zo0r/react-native-push-notification --save

// For ios
npm install https://github.com/react-native-community/react-native-push-notification-ios --save
```

We installed the libraries and now, we will implement them android and ios in native side firstly.

### IOS implementation: 

According to [React Native Community](https://github.com/react-native-community/react-native-push-notification-ios), There are a couple of cases for linking. Choose the appropriate one.

* react-native >= 0.60

The package is automatically linked when building the app. All you need to do is:

```shell
cd ios && pod install
```

* react-native <= 0.59

```shell
react-native link @react-native-community/push-notification-ios
```

* upgrading to react-native >= 0.60

First, unlink the library. Then follow the instructions above.

```shell
react-native unlink @react-native-community/push-notification-ios
```

We linked the library to our project. And now, we should add native code blocks. Import this modules like this.

```swift
#import <RNCPushNotificationIOS.h>
#import <UserNotifications/UserNotifications.h>
```

After importing modules, we ready to add listeners of notification center modules to our react native project.

<!-- <script src="https://gist.github.com/keremcubuk/7690448f12f5ecd168161c16a59c8e8e.js"></script> -->
```swift
// AppDelegate.m

// .... Other Code Blocks
NSURL *jsCodeLocation = [[RCTBundleURLProvider sharedSettings] jsBundleURLForBundleRoot:@"index" fallbackResource:nil];
    [ReactNativeNavigation bootstrap:jsCodeLocation launchOptions:launchOptions];

  // define UNUserNotificationCenter
    UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];
    center.delegate = self;

    return YES;
}
// .... Other Code Blocks

// Required to register for notifications
- (void)application:(UIApplication *)application didRegisterUserNotificationSettings:(UIUserNotificationSettings *)notificationSettings
{
  [RNCPushNotificationIOS didRegisterUserNotificationSettings:notificationSettings];
}
// Required for the localNotification event.
- (void)application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification
{
  [RNCPushNotificationIOS didReceiveLocalNotification:notification];
}

//Called when a notification is delivered to a foreground app.
-(void)userNotificationCenter:(UNUserNotificationCenter *)center willPresentNotification:(UNNotification *)notification withCompletionHandler:(void (^)(UNNotificationPresentationOptions options))completionHandler
{
  NSLog(@"User Info : %@",notification.request.content.userInfo);
  completionHandler(UNAuthorizationOptionSound | UNAuthorizationOptionAlert | UNAuthorizationOptionBadge);
}

@end
```

We are ready to use in react-native side. Before going to react-native side, let's look at the Android native implementation.

### Android Implementation:

Linking is nearly same as IOS implementation. Let's investigate it.

* react-native <= 0.59

```shell
react-native link @react-native-community/push-notification
```

* upgrading to react-native >= 0.60

First, unlink the library. Then follow the instructions above.

```shell
react-native unlink @react-native-community/push-notification
```

To access manual implementation of Android, you can follow [this instruction](https://github.com/zo0r/react-native-push-notification).


After linking and implementing `react-native-push-notification` library, we are ready to create a new file which helps you send push notification via JavaScript. With this file, we will send notification to device notification center and show in app. Firstly, create a new file in your app which name is `LocalNotificationService.js` file under `src/utils` folder.

**Import Push Notification:**

```javascript
import PushNotification from 'react-native-push-notification';
import { Platform } from 'react-native';
```

**Create LocalNotificationService Class:**

This code block is helps to init `Notification Service` in your react native project.

```javascript
export default class LocalNotificationService {
    static init() {
        LocalNotificationService.onNotification = notification => {
            if (Platform.OS === 'android' && notification.subject != null && notification.subject !== '') {
                PushNotification.localNotification({
                    title: notification.subject,
                    message: notification.body,
                });
            }
        };
    }
}
```

And now, we should add configure function to connect native notification center of your device.

```javascript
static configure() {
    PushNotification.configure({
        onNotification: notification => {
            if (LocalNotificationService.onNotification) {
                LocalNotificationService.onNotification(notification);
            }
        },
        requestPermissions: true,
        popInitialNotification: true,
    });
}
```

This is the good one, are you ready for write to `sendLocalNotification()` function?

If your are answer is YES. Let's create a new function inside the `LocalNotificationService` class.

```javascript
static sendLocalNotification(title, message) {
    PushNotification.localNotification({
        title, // (optional) // Your content title
        message, // (required) // Your content message. It is required for notification.
    });
}
```

As you see at the top, you should send two parameter all the time. One of them is `optional`, and the other one is `required`. This required parameter is `message`, message parameter shows the your content inside the notification message.

If you want to remove all notification. You can write this function, which name is `cancelAll()`.

```javascript
static cancelAll() {
    PushNotification.cancelAllLocalNotifications();
}
```

Final view of our `LocalNotificationService.js` file.

```javascript
import PushNotification from 'react-native-push-notification';
import { Platform } from 'react-native';

export default class LocalNotificationService {
  static init() {
    LocalNotificationService.onNotification = notification => {
      if (Platform.OS === 'android' && notification.subject != null && notification.subject !== '') {
        PushNotification.localNotification({
          title: notification.subject,
          message: notification.body,
        });
      }
    };
  }


  static configure() {
    PushNotification.configure({
      onNotification: notification => {
        if (LocalNotificationService.onNotification) {
          LocalNotificationService.onNotification(notification);
        }
      },
      requestPermissions: true,
      popInitialNotification: true,
    });
  }

  static sendLocalNotification(title, message) {
    PushNotification.localNotification({
      title, // (optional) // Your content title
      message, // (required) // Your content message. It is required for notification.
    });
  }

  static cancelAll() {
    PushNotification.cancelAllLocalNotifications();
  }
}
```

We write our all functions are ready to use. We just import and call the function to send notification. I just write a new button in my component and implement the `LocalNotificationService.js`. You can add and import where you want.

**Import LocalNotificationService:**

```javascript
import LocalNotificationService from '../utils/LocalNotificationService';
```

**Init LocalNotificationService**

```javascript
// Just init your project root one time.
LocalNotificationService.init();
LocalNotificationService.configure();
```

**Create a click function for send notification:**

```javascript
notify() {
    LocalNotificationService.sendLocalNotification('Notification Title', 'Notification Detail Content');
}
```

And use the function in a button like that:

```javascript
<Button title="Notify Me" onPress={() => this.notify()} />
```

Final result of my screen.

```javascript
import React from 'react';
import { View, Button, Text } from 'react-native';
import LocalNotificationService from '../../utils/LocalNotificationService';

// Just init your project root one time.
LocalNotificationService.init();
LocalNotificationService.configure();

export default class App extends React.Component {
  notify() {
    LocalNotificationService.sendLocalNotification('Notification Title', 'Notification Detail Content');
  }

  render() {
    return (
      <View>
        <Button title="Notify Me" onPress={() => this.notify()} />
      </View>
    );
  }
}
```

Now, click the `Notify Me` button and see the magic :D

![Final Result](https://media.giphy.com/media/LpiZjLKPUZgoAwQU6N/giphy.gif)

Thank you for read this blog. I shared my experience with you. And I will all the time. If you have a question, you can send a message or comment under this blog. Happy Coding <3