# SIBOAT Android

This repository packages the supplied `SIBOAT_index_FIXED.html` controller inside a native Android WebView.

## Important

The controller HTML is kept as the app's main UI and communication layer. The Android project adds only the native container required to build/install it as an APK.

The HTML currently uses:
- Supabase over HTTPS
- ESP32 HTTP endpoints
- ESP32 WebSocket at port 81
- `10.90.102.50` and `siboat.local`
- browser local storage
- file upload controls

Android is configured for Internet access and cleartext local HTTP so the existing ESP32 connection path can continue to work.

## GitHub build

1. Create a new GitHub repository.
2. Upload this entire project, preserving folders.
3. Commit to the `main` branch.
4. Open **Actions**.
5. Select **Build SIBOAT Android APK**.
6. If GitHub did not start it automatically, choose **Run workflow**.
7. Wait for the workflow to finish.
8. Open the completed workflow run.
9. Under **Artifacts**, download `SIBOAT-debug-apk`.
10. Extract it on the Android phone and install `app-debug.apk`.

No Android Studio or local computer is required for this build workflow.

## Files

- `app/src/main/assets/index.html` — the supplied SIBOAT controller HTML.
- `app/src/main/java/com/siboat/controller/MainActivity.java` — Android WebView wrapper and native permission/file handling.
- `app/src/main/AndroidManifest.xml` — Internet, camera, cleartext local-network configuration.
- `app/build.gradle` — Android application build configuration.
- `build.gradle` — Android Gradle Plugin version.
- `settings.gradle` — project configuration.
- `gradle.properties` — Gradle/Android settings.
- `app/src/main/res/*` — app resources.
- `.github/workflows/build-apk.yml` — GitHub Actions APK build.
- `README.md` — phone/GitHub build instructions.

The supplied ESP32 `.ino` firmware files and firmware ZIPs are not required to compile the Android APK. They remain firmware for the physical SIBOAT controller and should not be bundled into the Android app unless you later want a separate firmware-release workflow.
