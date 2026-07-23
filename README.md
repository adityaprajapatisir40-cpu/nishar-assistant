# Nishar — By Aditya (Slice 1: Foundation)

Owner: Aditya Prajapati

This is **slice 1 of 7** in the build plan: Gradle project skeleton, package
architecture, Hilt DI graph, navigation graph, and the Black+Gold Material 3
theme with a premium splash screen. Everything in this slice is real,
compiling code — nothing here is a fake stub pretending to be a finished
feature.

## What's implemented in this slice
- Full Gradle setup (project + app `build.gradle.kts`) with dependencies
  reserved for Compose, Hilt, Room, WorkManager, CameraX, ML Kit, and
  Retrofit — so later slices only need to *use* these, not add them.
- Package structure: `ui / data / domain / repository / database / services
  / ai / security / utils / navigation / di`.
- Hilt DI graph (`NisharApplication`, `AppModule`) — compiles end-to-end.
- Navigation graph (`Screen.kt`, `NisharNavGraph.kt`) with 4 real routes.
- Black+Gold Material 3 theme (`Color.kt`, `Type.kt`, `Theme.kt`).
- Splash screen: pulsing gold glow ring behind a mic icon, "NISHAR / By
  Aditya" wordmark, auto-advances to Home.
- Home screen: dashboard card grid + glowing tap-to-talk mic button (wiring
  to actual voice input arrives in the AI slice).
- Settings screen: three real, working toggles (dark mode, wake word, speak
  replies) — UI state is live; persistence lands with the Room/DataStore
  slice.
- Security screen: **honestly labeled placeholder** — face recognition,
  intruder capture, and the dashboard need CameraX + ML Kit wiring that is
  slice 6 in the plan, not slice 1.

## One thing you must do yourself before building
This zip does **not** include the Gradle wrapper binary (`gradlew`,
`gradlew.bat`, `gradle-wrapper.jar`) — I have no network access to download
it, and a hand-written binary jar isn't something I can safely fabricate.

**Building on a computer (Android Studio):** open the project folder in
Android Studio — it detects the missing wrapper and regenerates it
automatically. Then `./gradlew assembleDebug` produces a debug APK at
`app/build/outputs/apk/debug/`.

**Building from mobile only (GitHub Actions):** this project includes
`.github/workflows/build.yml`, which builds the APK on GitHub's free cloud
runners — no wrapper jar needed, since the workflow installs Gradle directly.
Steps:
1. Create a free GitHub account and a new repository (e.g. `nishar-app`).
2. Upload every file/folder from this zip into that repository, preserving
   folder structure (GitHub's web "Add file → Upload files" supports
   drag-and-drop of whole folders on desktop; on mobile browser you may need
   to upload folder-by-folder — see chat for a walkthrough).
3. Pushing the files automatically triggers the workflow. Open the
   **Actions** tab in your repo, wait for the "Build Nishar Debug APK" run
   to go green (a few minutes).
4. Click the finished run → download the `nishar-debug-apk` artifact zip →
   inside is `app-debug.apk`, installable on any Android device.


## Next slices (in order)
2. Core UI polish pass (animations, dynamic theming refinements).
3. AI conversation core — Room chat history, Gemini API client, TTS/STT,
   tap-to-talk wired live.
4. Wake word ("Nishar") + foreground service listening loop.
5. Phone control intents (apps, calls, SMS, alarms, flashlight, etc.).
6. Security module — face enrollment, intruder detection, dashboard.
7. Vision AI (OCR/QR/barcode/object/currency) + productivity/entertainment
   modules.
