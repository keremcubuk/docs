# Real Device Metro

On Android 5.0+ devices connected via USB, you can use the adb command line tool to setup port forwarding from the device to your computer:

```shell
adb reverse tcp:8081 tcp:8081
```
