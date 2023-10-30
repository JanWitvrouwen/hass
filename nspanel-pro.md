# NSpanel Pro dirty guide

https://blakadder.com/nspanel-pro-sideload/

https://blakadder.com/android-panel-webview/

```
adb tcpip 5555
adb connect *IP*
adb install .\ultra-small-launcher.apk
adb shell input keyevent 3
adb install '.\de.robv.android.xposed.installer_3.1.5-43_minAPI15(nodpi)_apkmirror.com.apk'
adb push '.\xposed-v90-sdk27-arm64-beta3(1).tar' /sdcard/Download/
adb shell
su
mount -o rw,remount /system
cd /sdcard/Download/
tar -xvf xposed-v90-sdk27-arm64-beta3.tar
chmod a+x /sdcard/Download/xposed-v90-sdk27-arm64-beta3/META-INF/com/google/android/flash-script.sh
sh /sdcard/Download/xposed-v90-sdk27-arm64-beta3/META-INF/com/google/android/flash-script.sh
exit
adb reboot
adb shell input keyevent 3
```
*Check installation*
```
adb install '.\com.google.android.webview_95.0.4638.74-463807400_minAPI21(armeabi-v7a)(nodpi)_apkmirror.com.apk'
adb shell input keyevent 3
```
*Activate Dev mode*

*change webview*

*Uninstall bloatware*

```
adb shell
pm uninstall --user 0 com.eWeLinkControlPanel
pm uninstall --user 0 com.eWeLinkNSPro.dev
pm uninstall --user 0 com.rockchip.devicetest
pm uninstall --user 0 android.rockchip.update.service
pm uninstall --user 0 com.android.gl2jni
pm uninstall --user 0 com.smatek.test
pm uninstall --user 0 android.rk.RockVideoPlayer
pm uninstall --user 0 acr.browser.barebones
pm uninstall --user 0 org.chromium.webview_shell
pm uninstall --user 0 com.android.music
pm uninstall --user 0 com.android.nfc 
pm uninstall --user 0 com.DeviceTest
pm uninstall --user 0 com.cghs.stresstest
```
```
adb -e install .\nspanel-pro-tools-1.1.0-release.apk
adb -e install .\app-minimal-release.apk
adb shell input keyevent 3
```
*Open NSpanel pro tools and config*

```
adb shell input text BLA
```
