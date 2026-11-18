# Mind Lab

Mind Lab is an offline psychology learning app packaged for Android with Capacitor.

## Get a test APK

Push an app change to a non-`main` branch. In **Actions → Android APK**, open that branch's successful run and download **MindLab-test-apk** under **Artifacts**. Extract the ZIP and install `app-debug.apk` on Android. This debug build is for testing, not distribution. If it conflicts with an installed build signed with a different key, Android will require uninstalling that build first (which can delete its local app data).

## Publish a signed APK

In **Settings → Secrets and variables → Actions → Repository secrets**, configure:

| Secret | Value |
| --- | --- |
| `KEYSTORE_BASE64` | The base64-encoded Android release keystore |
| `KEYSTORE_PASSWORD` | Keystore password |
| `KEY_ALIAS` | Release key alias |
| `KEY_PASSWORD` | Key password |

Keep a secure backup of the release keystore and reuse it for every update. Never commit it or its passwords. If an APK for `com.mindlab.app` has already been distributed, reuse that APK's signing key and, if needed, set the repository variable `VERSION_CODE_OFFSET` so new Android version codes are higher than the last distributed APK's.

Once this workflow is on `main`, an app change pushed to `main` (including a PR merge) builds and publishes a signed release. To release without another commit, go to **Actions → Android APK → Run workflow**, select `main`, and enable **Publish a signed GitHub Release**. Leaving the option off only builds a test APK.

The verified, signed `MindLab-v*.apk` and its SHA-256 checksum are attached to the release under **Releases**. A failed signing step will not publish an APK.
