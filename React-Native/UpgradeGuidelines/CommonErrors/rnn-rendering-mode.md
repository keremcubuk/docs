# XCODE React Native Navigation imageWithTintColor:renderingMode

If you are using react-native-navigation v4. You must use Xcode11, if you use Xcode 10, you will get that error.

```javascript
node_modules/react-native-navigation/lib/ios/UIImage+tint.m:7:16 No visible @interface for 'UIImage' declares the selector 'imageWithTintColor:renderingMode:'
```

Open Ticket: https://github.com/wix/react-native-navigation/issues/5746