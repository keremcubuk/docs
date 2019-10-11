# Landroidx/swiperefreshlayout/widget/SwipeRefreshLayout Error - react-native-screens

If you get this error you should follow the steps.

```java
AndroidRuntime	FATAL EXCEPTION: mqt_native_modules
Process: com.rnnext, PID: 24380
java.lang.NoClassDefFoundError: 
Caused by: java.lang.ClassNotFoundException: com.facebook.react.views.swiperefresh.ReactSwipeRefreshLayout
	at java.lang.VMClassLoader.findLoadedClass(Native Method)
	at java.lang.ClassLoader.findLoadedClass(ClassLoader.java:742)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:362)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:312)
	at libcore.reflect.InternalNames.getClass(InternalNames.java:53)
	... 35 more
Caused by: java.lang.NoClassDefFoundError: Failed resolution of: Landroidx/swiperefreshlayout/widget/SwipeRefreshLayout;
```

Add this library as a depedency to your project:

```powershell
npm install react-native-screens --save
```

Link native modules this library ships with into your app:

```powershell
react-native link react-native-screens
```


Add the following two lines to `dependencies` section in `android/app/build.gradle.` You likely already have `appcompat` dependency listed there in which case you need to make sure that you use version `1.1.0-rc.01`:

```java
implementation 'androidx.appcompat:appcompat:1.1.0-rc01'
implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.1.0-alpha02'
```

And Finally, rebuild your project.