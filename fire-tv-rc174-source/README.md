# JTPlay Fire TV RC 174 corresponding source

Android package `com.jtplay.app`, version name `0.1.0`, version code `3174`, ARMv7 and ARM64. Original unsigned APK SHA-256: `024c27ccdc217efc97a86380285c347da1d634b69d8027eb319058cd5939f096`.

Download the [published Android base source archive, notices, GPLv3 license and checksums](https://github.com/Adaptabull/JTPlay-public/releases/tag/build-173-android-source). The source archive SHA-256 is `98409a8fdd4b0fefe2f7a55d805cf9554af7b92d411d6bf4b19a5cd6d7ae8e16`. Extract `main-source.tar` into an empty directory and apply [the RC 174 patch](JTPlay-FireTV-RC174.patch) with `git apply`. The RC 174 patch includes the RC 173 changes. Apply only the RC 174 patch. The tar contains the full Android application base at revision `a785cdcbae633e0044b0720b5bc8eff244fb33d2`.

Follow the base archive's `BUILDING-FIREOS.md` for toolchain requirements, package locks and native recipes, with the following RC 174 steps. Use Flutter 3.47.1 (engine `5d531788691ec3404cac0cee66ead4007b177363`), JDK 21, Android SDK 36, Build Tools 36.1.0, NDK 29.0.14206865, CMake 4.1.2 and the Gradle wrapper. Run `flutter pub get` and ensure `android/app/src/main/java/io/flutter/plugins/GeneratedPluginRegistrant.java` exists. Set `AMAZON=1` in the build environment and run:

```sh
flutter build apk --release --no-pub --target-platform android-arm,android-arm64 --build-name 0.1.0 --build-number 174 --dart-define=ENABLE_SENTRY=false --dart-define=SUPPORTER_MODE=unlocked
```

## Native bridge source and notices

The rebuilt `libasskt.so` uses the unchanged JNI sources, CMake and fetch script under `android/libass/src/main/cpp` and the same checksum-pinned combined libass archive. The base bundle includes libass 0.18.3, its constituent dependencies and Meson patches. See `LIBASS-PROVENANCE.md`.

The rebuilt `libdovi_bridge.so` uses the unchanged bridge and libdovi header under `android/app/src/main/cpp`. The base bundle includes the locked libdovi sources, Rust crates and the prebuilt recipe. The rebuilt `libffmpegJNI.so` uses the unchanged FFmpeg JNI sources and CMake in the same directory and links the FFmpeg libraries selected by the unchanged `mpv-build.lock.json`. The base bundle includes the pinned Android mpv/FFmpeg source, build recipes and patches.

The archived bridge files and build scripts were compared directly with the RC 174 checkout and match after line-ending normalization. `pubspec.lock` also matches. The rebuilt `libdartjni.so` is covered by the locked `jni` 0.14.2 source archive. The base package retains the applicable native and Flutter notices, original copyright and GPL attribution. See its `ANDROID-COMPLIANCE.md` and `SHA256-INVENTORY.json`. The RC 174 supplement and linked base archive together provide the source delivery.
