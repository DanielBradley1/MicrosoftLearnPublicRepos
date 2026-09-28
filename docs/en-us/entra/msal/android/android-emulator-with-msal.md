<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/android-emulator-with-msal -->
<!-- Sitemap-Last-Modified: 2025-03-06 -->

# Using Android Emulator with MSAL Android

In order to use MSAL, you'll need an emulator to test with that supports Chrome or Chrome custom tabs. In the main IDEs, this can be accomplished:

- In Visual Studio, use an emulator with Android 25+.
- In Android Studio, use a Pixel or Nexus emulator with Android 21+.

## Manual Steps

1. Make sure you're using an emulator with Android 21+.
2. Install the latest Chrome APK from a reputable site. For example, [Chrome Browser](https://www.apkmirror.com/apk/google-inc/chrome/) on [APK Mirror](http://www.apkmirror.com/apk/google-inc/chrome/). Make sure to pick the right APK for your Android version and emulator architecture.
3. Drag the APK file to your emulator, this will automatically install the app. Go to the app list, and verify Chrome was installed.

## Troubleshooting

- You may need to disable Hyper-V in some situations and enable HAXM or AEHD. For more information on how to enable HAXM or AEHD, see [How to enable hardware acceleration with Android emulators \(Hyper-V & AEHD\)](https://learn.microsoft.com/en-us/dotnet/maui/android/emulator/hardware-acceleration).
- The Android emulator deployments can take quite a long time on certain machines if it's the first time.
- Known issue: Some Android emulator instances running on Windows 10 intermittently fail with `java.io.EOFException`. Suggested workaround is to use a physical device and/or an emulator hosted in another operating environment. [Link to issue](https://github.com/square/okhttp/issues/1517).

## Help

If the above steps don't work for you or you encounter some trouble, please open a Github issue or post on Stackoverflow.
