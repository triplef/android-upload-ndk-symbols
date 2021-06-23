Upload Android NDK Symbols to Firebase Crashlytics
==================================================

This Gradle project allows uploading Android NDK native library symbols to Firebase Crashlytics independent from the build process of your app.

It is intended to be used e.g. during a "publish" task on a CI server in order to upload symbols only for builds that are published. This can significantly speed up builds if your app has a lot of native code, as generating symbol files and uploading them to Firebase can be a slow process.

Usage
-----

First, copy your `google-services.json` into this folder. This is required for the Firebase Crashlytics Gradle plugin to have access to your Google App ID in order to associate the symbols with your app.

Then call the Gradle task with your application identifier and the path to a folder containing your unstripped native libraries:
```
./gradlew uploadCrashlyticsSymbolFileRelease -PapplicationId=com.example.app -PunstrippedNativeLibsDir=/path/to/unstripped-native-libs
```

The unstripped native libraries can usually be found in the following location of your Android build:
`build/intermediates/merged_native_libs/release/out/lib/`
