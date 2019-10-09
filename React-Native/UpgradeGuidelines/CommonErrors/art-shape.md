# ART - ArtShape Error

## What is it?
React Native ART is a library which supported by @react-native-community. This library helps to develop animated things. 

> For Example: Loaders, Shaking Buttons etc.

## Where it used?
- react-native-circular-progress
- react-native-progress

## Error

![ArtShape](/assets/images/artshape-error.png)

If you see this error while developing your project. You have follow these steps:

Firstly: 
```javascript
    npm install @react-native-community/art --save
```

```terminal
    cd ios
    pod install
```


#### iOS
And then:
Delete your installed app in your iOS simulator. After that in your Xcode > Product > Clean Build Folder

Finally: 
Rebuild your project in Xcode


### Android
And then:
Delete your installed app in your android emulator. After that gradle sync.

Finally:
Rebuild your project in Android Studio.