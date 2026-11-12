# Install/build v3.7.5

1. Extract this ZIP.
2. Upload the ZIP contents to the root of the GitHub repository (the `settings.gradle`, `app/`, `tools/`, and `.github/` paths must be at repository root).
3. Open Actions and run `Build OHLI Social Client APK`.
4. Download artifact `OHLI-Social-Client-APK-v3.7.5`.
5. Install `app-debug.apk` on Vivo Android Oreo. The client package remains `com.ohli.social.client`; keep the old server package installed.
6. In OHLI Settings, tap `Notifikasi aplikasi Android` to run a native test or open Android notification settings.
7. For diagnostics, use the existing OHLI diagnostic action and copy the JSON showing HTTP statuses and last sync result.

The APK has not been compiled or physically tested from this environment. A successful GitHub Actions build is still required.
