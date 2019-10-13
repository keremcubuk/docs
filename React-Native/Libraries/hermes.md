# Hermes - JavaScript Engine for React Native
## What is hermes?
Hermes is a JavaScript engine designed for Android platform by Facebook Engineers on July 21, 2019.  It’s a small and lightweight optimized for running React Native on Android. 

> `Important Note:` This technology only use after react-native 0.60.4 and laters.

## How does it work?

Traditional Javascript engines compile the code after the application is installed. So it compiles bytecode by compiling javascript codes during runtime. This causes delays in application startup.

![Hermes Engine Gif](/assets/images/hermes.gif)

`Hermes` generates bytecode during the creation of the application. There will be plenty of time to make this process more efficient.

## What are the benefits?
- Shortens the initial opening time of the application.
- Reduces the size of the application apk(on Android, APK size)
- Provides efficient memory usage.
- It can be easily integrated.

![Hermes Engine Stats](/assets/images/hermesstats.jpg)

## Why is it designed only for the Android platform?
Because Hermes is optimized for mobile apps, facebook engineers say that `"we do not have plans to integrate it with any browsers or with server infrastructure such as Node.js. Existing JavaScript engines remain preferable in those environments."`

### Why cannot use in iPhones(iOS)?
Apple, requires the use of `V8 JavaScript engine` on their devices. For this reason, custom Javascript engines can be used on the Android platform. 

## How to use Hermes?

```gradle
// android/app/build.gradle,

  project.ext.react = [
      entryFile: "index.js",
-     enableHermes: false
+     enableHermes: true
  ]
```

```java
// You must clean and rebuild after can the gradle files.

  cd android && ./gradlew clean
```

> `Note:` If you do not clean up your project after making changes, your application may experience a constant crash during the opening.


## For more details:

[![android-developers](https://img.youtube.com/vi/zEjqDWqeDdg/0.jpg)](https://youtu.be/zEjqDWqeDdg)


## Resources:

- [React Native Integration](https://facebook.github.io/react-native/docs/hermes/)
- [Facebook Engineering](https://engineering.fb.com/android/hermes/)
