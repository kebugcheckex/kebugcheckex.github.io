---
title: Extract APKs from Android System using ADB
category: android
layout: post
tags:
- android
- adb
- apk
---

Sometimes developers needs to extract APK files from an Android phone, for the purpose of malware analysis, etc. This article describes how to do that with the ADB tool.

<!--more-->

## Prerequisites

In order to extract APK files from Android system, you'll need the `adb` tool. That comes with the Android SDK. If you don't have Android SDK installed, please refer to its [official documentation](https://developer.android.com/studio/).

With your phone connected through USB, run `adb devices` to make sure that the device is recognized. You may also need to accept some permissions on your phone the first time you connect to it.

## Steps

The first step is to get the package name. For example, if you want to extract the Twitter APK, run the following command

```
$ adb shell pm list packages | grep twitter
package:com.twitter.android
```

Now we have the package name as `com.twitter.android`. The next step is to get the file path,

```
$ adb shell pm path com.twitter.android
package:/data/app/com.twitter.android-gOLJpvoLzi9DRtrc99jlqA==/base.apk
package:/data/app/com.twitter.android-gOLJpvoLzi9DRtrc99jlqA==/split_config.arm64_v8a.apk
package:/data/app/com.twitter.android-gOLJpvoLzi9DRtrc99jlqA==/split_config.xxhdpi.apk
package:/data/app/com.twitter.android-gOLJpvoLzi9DRtrc99jlqA==/split_config.fr.apk
```

Note that you will likely find a few outputs, where the first one is `base.apk` while the other ones starts with `split_config`. This is an Android feature that aims to reduce APK file size by spliting parts of the app that targets different devices. To find out more about splitting apks, read the documentation at [Build Multiple APKs](https://developer.android.com/studio/build/configure-apk-splits). Depending on your needs, you may only need the base apk, or all of them. Use the following command to extract them

```
$ adb pull /data/app/com.twitter.android-gOLJpvoLzi9DRtrc99jlqA==/base.apk path/to/place/the/apk
```

Note that some shell environment may interpret the equal sign `=` in the path differently, causing weird errors. In that case you can quote the APK file path to ensure that it is parsed as a string literal.

## Reference

See original discussions on [Stackoverflow](https://stackoverflow.com/questions/4032960/how-do-i-get-an-apk-file-from-an-android-device).
