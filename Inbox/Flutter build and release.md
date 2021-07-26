---
title : Flutter build and release
date : 2021-07-24_Sat 21:54
aliases : [build, release]
---
Source Type :: #📥/📄 <br>
Source URL :: [Build and release an Android app](https://flutter.dev/docs/deployment/android)<br>
Source Author :: [[@Flutter]]<br>
Note Type :: <br>
Topics :: [[🍃Flutter MOC]]<br>
Parent Link :: [[🍃Flutter MOC]]<br>

---
# Flutter build and release


## Adding a launcher icon #🚧 
> TODO: Under Construstion


## Enabling Material Components
1. Add the dependency on Android’s Material in `<my-app>/android/app/build.gradle`:

```gradle
dependencies {
    // ...
    implementation 'com.google.android.material:material:<version>'
    // ...
}
```

> To find out the latest version, visit [Google Maven](https://maven.google.com/web/index.html#com.google.android.material:material).

2. Set the theme in `<my-app>/android/app/src/main/res/values/styles.xml`:

```gradle
- <style name="LaunchTheme" parent="Theme.AppCompat">
+ <style name="LaunchTheme" parent="Theme.MaterialComponents.NoActionBar">
```


## Signing the app
```shell
$ keytool -genkey -v -keystore ~/upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

### Reference the keystore from the app

Create a file named `[project]/android/key.properties` that contains a reference to your keystore:

```key.peoperties
storePassword=<password from previous step>
keyPassword=<password from previous step>
keyAlias=upload
storeFile=<location of the key store file, such as /Users/<user name>/upload-keystore.jks>
```

### Configure signing in gradle

Configure gradle to use your upload key when building your app in release mode by editing the `[project]/android/app/build.gradle` file.

1. Add the keystore information from your properties file before the `android` block:

```gradle
   def keystoreProperties = new Properties()
   def keystorePropertiesFile = rootProject.file('key.properties')
   if (keystorePropertiesFile.exists()) {
       keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
   }

   android {
         ...
   }
```
> Load the `key.properties` file into the `keystoreProperties` object.


2. Find the `buildTypes` block:

```gradle
   buildTypes {
       release {
           // TODO: Add your own signing config for the release build.
           // Signing with the debug keys for now,
           // so `flutter run --release` works.
           signingConfig signingConfigs.debug
       }
   }
```

*And replace it with the following signing configuration info:*

```gradle
   signingConfigs {
	   release {
		   keyAlias keystoreProperties['keyAlias']
		   keyPassword keystoreProperties['keyPassword']
		   storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
		   storePassword keystoreProperties['storePassword']
	   }
   }
   buildTypes {
	   release {
		   signingConfig signingConfigs.release
	   }
   }
```

*And run the command:*
```shell
$ flutter clean
```


## Reviewing the app manifest #🚧
Review the default [App Manifest](https://developer.android.com/guide/topics/manifest/manifest-intro) file, `AndroidManifest.xml`, located in `[project]/android/app/src/main` and verify that the values are correct, especially the following:

### application
Edit the `android:label` in the [`application`](https://developer.android.com/guide/topics/manifest/application-element) tag to reflect the final name of the app.

### uses-permission
Add the [`permission`](https://developer.android.com/guide/topics/manifest/uses-permission-element) if your application code needs some permissons.


## Reviewing the build configuration

Review the default [Gradle build file](https://developer.android.com/studio/build/#module-level), `build.gradle`, located in `[project]/android/app` and verify the values are correct, especially the following values in the `defaultConfig` block:

> `applicationId`<br>
> Specify the final, unique (Application Id)[appid](https://developer.android.com/studio/build/application-id)

> `versionCode` & `versionName`<br>
> Specify the internal app version number, and the version number display string. You can do this by setting the `version` property in the pubspec.yaml file. Consult the version information guidance in the [versions documentation](https://developer.android.com/studio/publish/versioning).

> `minSdkVersion`, `compilesdkVersion`, & `targetSdkVersion`<br>
> Specify the minimum API level, the API level on which the app was compiled, and the maximum API level on which the app is designed to run. Consult the API level section in the [versions documentation](https://developer.android.com/studio/publish/versioning) for details. `buildToolsVersion`<br><br>
> Specify the version of Android SDK Build Tools that your app uses. Alternatively, you can use the Android Gradle Plugin in Android Studio, which will automatically import the minimum required Build Tools for your app without the need for this property.


## Building the app for release
Two ways to build.
- App bundle => Release to Play Store
- APK (==test preferred==) => Something else

### Build an app bundle
```shell
$ cd [project]
$ flutter build appbundle
	($ flutter build)
```

### Test the app bundle #🚧
TODO: Under Construction


### Build an APK
```shell
$ cd [project]
$ flutter build apk --aplit-per-abi
	(default is $ flutter build apk --release)
```

### Install an APK on a device
#### Use Hardware to test
```shell
$ sudo usermod -aG plugdev $LOGNAME
$ reboot
```

```shell
$ sudo apt install android-sdk-platform-tools-common
```

```shell
$ ~/Android/Sdk/platform-tools/adb devices
> List of devices		attached
> 43aa44f5				device
```

```shell
$ flutter install
```

##### Connect to your device using USB

## Publishing to the Google Play Store #🚧

## Updating the app’s version number #🚧