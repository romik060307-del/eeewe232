# OHLI Social Android Client v3.7.5

## Fokus: notifikasi native, bukan Web Notifications

- Menambahkan adapter Notification Android pada WebView melalui `OHLI_ANDROID`.
- Menyuntikkan kompatibilitas `window.Notification` agar script web lama yang memanggil `Notification.requestPermission()` atau `new Notification()` diarahkan ke notifikasi Android.
- Mengubah label pengaturan dari izin notifikasi browser menjadi notifikasi aplikasi Android.
- Menangkap klik pengaturan notifikasi di fase capture agar pesan "Browser ini tidak menyediakan notifikasi web" tidak muncul di dalam APK.
- Menambahkan pemeriksaan apakah notifikasi aplikasi dan kanal pesan/panggilan Android aktif.
- Tombol pengaturan mengirim tes notifikasi native atau membuka pengaturan notifikasi Android.
- Menambahkan menu Diagnostik notifikasi & koneksi untuk melihat status service, izin, versi WebView, dan respons endpoint API.
- Menambahkan pintasan izin berjalan di latar belakang untuk membantu perangkat Vivo mempertahankan layanan sinkronisasi.
- Menyinkronkan sesi `localStorage` ke `SharedPreferences` native setelah login dan saat halaman aktif agar layanan latar belakang memiliki token/nomor akun.
- Menghindari pemanggilan start service berulang ketika sesi tidak berubah.
- Diagnostik menyimpan waktu dan hasil polling terakhir untuk membedakan masalah izin dari endpoint API.
- Versi aplikasi: `3.7.5`, versionCode `63`, applicationId tetap `com.ohli.social.client`.

## Batas yang tetap berlaku

- Android WebView tidak menyediakan Web Notifications/Push API standar seperti browser Chrome. APK menggunakan adapter native Android sebagai gantinya.
- Polling tujuh detik hanya dapat bekerja selama foreground service masih diizinkan sistem. Force-stop, pembatasan OEM, atau penghentian service dapat menghentikannya.
- Notifikasi pesan/panggilan hanya dapat masuk bila endpoint `/api/messages`, `/api/calls`, `/api/notifications` pada `https://ohlisocial.netlify.app/` benar-benar menjawab JSON API dengan sesi akun yang valid.
- FCM membutuhkan konfigurasi proyek Firebase dan pengiriman push dari backend; kredensial tidak dibuat atau direka dalam source ini.
- Belum dilakukan build APK maupun uji pada perangkat fisik dalam lingkungan ini.
