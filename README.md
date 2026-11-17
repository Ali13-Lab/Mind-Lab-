# Mind Lab: APK build

1. Upload this whole folder to a GitHub repository (main branch).
2. Go to the repository's Actions tab, choose "Build Mind Lab APK", press "Run workflow".
3. When the run finishes (about 5 to 10 minutes), open the run and download the artifact "mind-lab-debug-apk". It contains app-debug.apk.
4. Install the APK on your phone (allow installation from unknown sources for the browser or file app you use).

The app ID is com.shinapps.mindlab. Change it in capacitor.config.json before the first build if you want a different ID.
The debug APK is for testing. A release APK needs a signing key, which we will add later.
