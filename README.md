# Anggaran Keluarga

Aplikasi pencatatan keuangan keluarga dengan Google Sheets sebagai database dan Google Apps Script sebagai aplikasi web. Folder ini disiapkan sebagai source code yang bisa diunggah ke GitHub untuk version control/backup.

## Fitur
- Ringkasan pemasukan, pengeluaran, dan sisa anggaran bulanan.
- Pencatatan pemasukan/pengeluaran.
- Riwayat transaksi dan identitas email pencatat.
- Progress pemakaian anggaran per kategori.
- Tampilan responsif untuk ponsel dan desktop.
- Allowlist dua akun Google pada backend.

## Catatan penting tentang GitHub Pages
Versi ini menggunakan `google.script.run`, API yang hanya tersedia saat halaman HTML disajikan oleh Google Apps Script. Karena itu, **unggah source ke GitHub untuk penyimpanan versi**, lalu jalankan aplikasi melalui deployment Google Apps Script. File `Index.html` harus ditambahkan sebagai file HTML bernama `Index` di editor Apps Script. GitHub Pages saja tidak dapat menjalankan `google.script.run`.

Jika ingin halaman benar-benar di-host di GitHub Pages, arsitektur autentikasi dan API perlu diganti (jangan menaruh password/token rahasia di JavaScript publik).

## Persiapan
1. Buat Google Spreadsheet bernama `Anggaran Keluarga`.
2. Salin ID spreadsheet dari URL: `https://docs.google.com/spreadsheets/d/ID_SPREADSHEET/edit`.
3. Buka https://script.google.com dan buat project baru.
4. Salin `apps-script/Code.gs` ke file `Code.gs`.
5. Buat file HTML bernama `Index`, lalu salin isi `Index.html` dari folder utama.
6. Di `Code.gs`, ganti `SPREADSHEET_ID`, `EMAIL_KAMU@gmail.com`, dan `EMAIL_ISTRI@gmail.com` dengan data sendiri.
7. Atur zona waktu project ke `Asia/Jakarta`.
8. Jalankan `setupDatabase()` dari editor Apps Script, lalu selesaikan otorisasi.
9. Bagikan spreadsheet kepada akun Google pasangan sebagai Editor.
10. Deploy sebagai Web app. Uji kedua akun. Jika `Session.getActiveUser().getEmail()` kosong atau akun tidak terbaca, jangan menonaktifkan pemeriksaan akses; periksa konfigurasi deployment dan akses akun terlebih dahulu.

## Mengunggah ke GitHub
1. Buat repository baru, misalnya `anggaran-keluarga`.
2. Upload `README.md`, folder `apps-script/`, dan `Index.html`.
3. Jangan pernah mengunggah ID/token/password rahasia atau data transaksi keluarga ke repository publik.

## Anggaran awal
Anggaran awal berjumlah Rp6.000.000/bulan. Nilainya bisa diedit di tab `Budgets` setelah database dibuat.

## Batasan
Source code belum terhubung ke spreadsheet atau akun Google Anda, belum di-deploy, dan belum diuji dengan akun Anda. Penggunaan dua akun harus diverifikasi pada deployment aktual sebelum dipakai untuk data keuangan pribadi.
