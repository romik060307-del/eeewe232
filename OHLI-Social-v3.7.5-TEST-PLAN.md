# OHLI Social Client v3.7.5 — Test Plan

## Source checks
1. Run `node tools/client-source-verify.mjs`.
2. Parse `AndroidManifest.xml` and `styles.xml` with Python XML parser.
3. Build with GitHub Actions and verify artifact is `OHLI-Social-Client-APK-v3.7.5`.

## Vivo Android Oreo device test
1. Install APK `com.ohli.social.client` without uninstalling server APK.
2. Login once and verify session remains after closing/reopening the app.
3. Open Settings > Tampilan & notifikasi > Notifikasi aplikasi Android.
4. Confirm the APK shows a native Android test notification; it must not show the browser unsupported warning.
5. Open Diagnostik notifikasi & koneksi and note the HTTP status and last sync state.
6. Use Izinkan berjalan di latar belakang and allow the requested system setting if Vivo shows it.
5. Send a text message from a second account while OHLI is backgrounded; verify Android notification, sound and reply action.
6. Verify sender receives `deliveredAt`/double-grey-tick after receiver service GET `/api/messages` succeeds.
7. Place an incoming call and verify a native call notification is shown.
8. Open Diagnostics and inspect `lastMessagesHttp`, `lastCallsHttp`, `lastSocialHttp`, `lastSyncState`, and timestamps.

## Interpretation
- If native test notification is absent, inspect Android app notification settings/channels.
- If test notification appears but message notifications do not, inspect API HTTP status and timestamps; likely endpoint/auth/routing issue.
- If HTTP is 404 or HTML, Netlify `/api/*` is not reaching the OHLI backend. Configure a real proxy/route to the current backend; do not point the app's poller to a changing tunnel URL without a stable endpoint.
- If sync timestamp stops updating after backgrounding, Vivo battery/background restrictions stopped the foreground service; allow background/autostart and disable battery optimization for OHLI.
- For notifications after Android force-stop/OEM termination, integrate FCM on both Android and backend.
