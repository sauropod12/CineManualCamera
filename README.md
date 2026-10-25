# Cine Manual — Android 10 camera project

An original, Blackmagic Camera-inspired manual-style video camera starter app for Android 10+ (API 29). It does not use Blackmagic's code, assets, name, or logo.

## Included in this starter
- Dark, cinema-style camera UI
- Rear-camera preview using Camera2
- MP4 video recording with AAC audio
- 4K selection when the camera advertises a compatible MediaRecorder output size; otherwise it falls back to 1080p or the largest available size
- 1080p/maximum resolution toggle
- H.264 and H.265/HEVC encoder selection (HEVC depends on device/encoder support)
- Saves clips to `Movies/CineManual` through MediaStore on Android 10+

## Build requirements
- Android Studio (current stable)
- JDK 17 for Android Gradle Plugin 8.7.3
- Internet access for the first Gradle sync (to download Gradle/Android dependencies)
- Android SDK Platform 35 installed through SDK Manager

## Build the APK
1. Extract `CineManualCamera.zip`.
2. Open the extracted `CineManualCamera` folder in Android Studio.
3. Let Gradle sync. If prompted, install Android SDK Platform 35 and use JDK 17.
4. Choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. Android Studio shows a link to the APK, normally at `app/build/outputs/apk/debug/app-debug.apk`.

This starter does not include the Gradle wrapper files; opening in Android Studio is the intended build path. Android Studio will configure/download the selected Gradle version during sync.

## Install and test on Samsung Galaxy Note 9 (SM-N960F, Android 10)
1. Transfer `app-debug.apk` to the phone.
2. Open it and allow installation from that source if Android asks.
3. Launch **Cine Manual**, then grant Camera and Microphone permissions.
4. Start with **1080p + H.264**. Record 10 seconds, stop, and check Gallery or `Movies/CineManual`.
5. Then test 4K and H.265 separately. Some camera/encoder combinations may fail even when an option appears in the UI; use 1080p/H.264 if that happens.

## Important limitations / next development steps
- This is a functional starter, not a full feature-for-feature clone. It currently uses automatic exposure and continuous video autofocus; manual ISO, shutter angle, white balance, focus pulling, LUTs, scopes, and advanced audio controls are not implemented yet.
- Camera2 stream combinations and supported resolutions vary by firmware. The app selects from sizes reported by the device, but recording must be tested on the actual phone.
- HEVC can fail if the device's camera/encoder combination does not support the selected size and frame rate. H.264 is the compatibility-first choice.
- 4K recording uses a high bitrate and can heat the phone or consume storage quickly. Test short clips first and keep the phone cool.
- No Blackmagic assets or proprietary code are included.

## Build without a computer using GitHub Actions
This project includes `.github/workflows/build-apk.yml`.
1. Create a GitHub account and a new repository.
2. Upload the contents of this project folder (including the hidden `.github` folder and its workflow file) to the repository.
3. Open the repository's **Actions** tab and enable Actions if GitHub asks.
4. Select **Build Cine Manual APK** on the left, press **Run workflow**, then press the green **Run workflow** button.
5. Open the completed run and download the `CineManual-debug-apk` artifact. GitHub may require you to download the artifact ZIP and then extract `app-debug.apk`.
The workflow uses a cloud Ubuntu runner and Java 17/Gradle 8.9 to compile the Android app.
