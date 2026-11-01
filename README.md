# Hykon Solar (Android)

The Hykon Solar Dashboard wrapped as an Android app. The dashboard is `app/src/main/assets/index.html`.

What the app adds over the web page:
- Share button: sends the day's summary as an image (with a WhatsApp-ready caption) or as plain text, straight to WhatsApp or any app.
- Sign-in pulls the data directly, so there is no file picker. Opening or sharing an .xlsx / .csv / .txt export into the app still works.
- Loaded days are remembered between launches.
- DessMonitor sign-in: enter the server, company key, username and password in the DessMonitor card, then pick a period (today, last 7 or 30 days, this or last month, this year, or a custom range) and press Fetch. Live refresh keeps today up to date every 1 to 10 minutes. The password is not saved.

## Build option A: GitHub (no Android Studio)
1. Create a new GitHub repository and push this folder to the `main` branch.
2. Open the repository's Actions tab, open the "Build APK" run, and download the `HykonSolar-apk` artifact.
3. Unzip it, copy `app-debug.apk` to the phone, open it, and allow "Install unknown apps" when asked.

## Build option B: Android Studio
1. Open this folder in Android Studio and let it sync (it downloads Gradle 8.9 and the Android SDK 34).
2. Build > Build APK(s). The file is `app/build/outputs/apk/debug/app-debug.apk`.
3. Or plug in the phone with USB debugging on and press Run.

Debug APKs use Android's standard debug signing key and are suitable for local installation/testing. Release builds are intentionally not signed by this repository.

## Signing and security
- The original project archive included a private signing keystore and hardcoded signing passwords. Those have been removed from this refreshed source archive.
- If that keystore/password has ever been pushed to a public or shared repository, treat it as compromised. Do not reuse it.
- For a production release, create a new private upload/release key and store its credentials in protected GitHub Actions secrets or an untracked local properties file. Never commit keystores, API keys, or passwords.

## Updating the dashboard
Replace `app/src/main/assets/index.html` with a newer copy and rebuild.
