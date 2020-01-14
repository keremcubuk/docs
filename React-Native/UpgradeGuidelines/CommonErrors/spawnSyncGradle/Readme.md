# spawnSync ./gradlew EACCES error when running react native project on emulator

If you getting this error. You should give permission to update gradle.

```powershell
error Failed to install the app. Make sure you have the Android development environment set up: https://facebook.github.io/react-native/docs/getting-started.html#android-development-environment. Run CLI with --verbose flag for more details.
Error: spawnSync ./gradlew EACCES
    at Object.spawnSync (internal/child_process.js:990:20)
    at spawnSync (child_process.js:601:24)
    at execFileSync (child_process.js:629:13)
    at runOnAllDevices (/Users/keremcubuk/dev/git/academy/react-native/react-native-user-address/solution/node_modules/@react-native-community/cli-platform-android/build/commands/runAndroid/runOnAllDevices.js:94:39)
    at process._tickCallback (internal/process/next_tick.js:68:7)
```

Run this code below:

```javascript
chmod 755 android/gradlew 
```
