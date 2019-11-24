# Firebase iOS Integration

In this document, we are going to add firebase to iOS app.

First of all, go to [firebase console](https://console.firebase.google.com/). And follow the steps below.

1. In your `Firebase Dashboard` click the `iOS Icon` on Banner. 

    ![firebase-dashboard](firebase-dashboard.png)

2. Complete the inputs and click the `Register App` button.

    ![step-1](step-1.png)

3. Download config file which name is `GoogleService-Info.plist`.

    ![step-2](step-2.png)

4. Add your `GoogleService-Info.plist` file under `yourApp > ios > yourAppName` folder.

    ![ios-path](add-plist.png)

5. Add `Firebase SDK` to your app.

    ![step-3](step-3.png)

- Go to `yourApp > ios > Podfile` file.

    ```java
    pod 'Firebase/Analytics'
    ```

- Next step of adding SDK. In your terminal `cd ios` and `pod install`.

6. Add initialization code.

    ![step-4](step-4.png)

- In your `appDelegate.m` file add Firebase.

    ```javaScript
    @import UIKit;
    @import Firebase;

    @implementation AppDelegate

    - (BOOL)application:(UIApplication *)application
        didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Firebase Integration: Start
        [FIRApp configure];
    // Firebase Integration: End

        return YES;
    }
    ```

7. Run your app. Wait for verification.

    ![step-5](step-5.png)

8. Run your app. After complete the verification click to `Continue to Console` button.

    ![step-6](step-6.png)

9. Your app added to Firebase successfully!

    ![step-7](step-7.png)
