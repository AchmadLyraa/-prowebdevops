
## URL Website Design

| **Role**              | **Endpoint URL**                     | **Fitur/Deskripsi**                                                                                                                                                                | **Mapping ke Tabel Database**                                                                              | **Catatan**                                                                                                     |
|-----------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| **Super Admin**       | `/super-admin`                       | Melihat statistik sistem secara keseluruhan, shortcut ke manajemen admin & lapangan, dan notifikasi penting                                                                         | - **users** (admin)<br>- **fields**<br>- Laporan bisa dihasilkan dari **bookings**, **payments**, dsb.      | Dashboard ini memberikan overview dari seluruh sistem                                                            |
| **Super Admin**       | `/super-admin/admin`                 | Menambahkan, mengubah, dan menghapus akun admin                                                                                                                                   | - **users** (dengan user_type: admin/super-admin)                                                          | Manajemen akun admin diatur melalui data pada tabel **users**                                                     |
| **Super Admin**       | `/super-admin/laporan`               | Mengakses laporan komprehensif penggunaan sistem, statistik pendapatan, jumlah booking, performa lapangan, dapat unduh laporan dalam PDF/Excel                                      | - **bookings**<br>- **payments**<br>- **fields**<br>- Data Loyalty (misal: **loyalty_programs**, **user_points**) | Laporan mengagregasi data dari beberapa tabel untuk analisa kinerja sistem                                           |
| **Admin**             | `/admin`                             | Ringkasan booking harian, mingguan, dan bulanan; notifikasi booking baru dan pembayaran; shortcut ke manajemen booking dan program loyalty                                           | - **bookings**<br>- **payments**<br>- **loyalty_programs** dan tabel poin terkait (**user_points**, dsb.)       | Dashboard admin fokus pada operasional booking dan transaksi                                                       |
| **Admin**             | `/admin/booking`                     | Melihat, menambah, mengubah, dan menghapus data booking pelanggan (filter berdasarkan tanggal dan status)                                                                            | - **bookings**                                                                                            | Aksi CRUD (Create, Read, Update, Delete) pada data booking                                                           |
| **Admin**             | `/admin/program-loyalty`             | Menambah, melihat, mengubah, dan menghapus program loyalty beserta ketentuan poin dan hadiah                                                                                        | - **loyalty_programs**                                                                                    | Fitur ini mendukung pengelolaan program loyalti agar pelanggan aktif                                                 |
| **Admin**             | `/admin/transaksi`                   | Memverifikasi pembayaran, melihat status pembayaran untuk booking, mengelola refund, melihat riwayat transaksi                                                                       | - **payments**                                                                                            | Transaksi keuangan langsung terhubung dengan data booking dan status pembayaran                                      |
| **Admin**             | `/admin/laporan`                     | Mengakses laporan booking (harian/mingguan/bulanan), statistik pendapatan per lapangan, dan aktivitas pelanggan, serta mengunduh laporan                                           | - **bookings**<br>- **payments**                                                                           | Mirip dengan laporan di dashboard super admin tetapi dengan detail untuk operasional harian                          |
| **Pengguna/Pelanggan**| `/pengguna`                          | Melihat daftar lapangan yang tersedia dan mendapatkan notifikasi status booking serta promo terbaru                                                                                 | - **fields**<br>- **field_images**                                                                          | Tampilan awal bagi pengguna untuk memilih lapangan yang diminati                                                     |
| **Pengguna/Pelanggan**| `/pengguna/profil`                   | Mendaftar, login, melihat dan mengubah informasi profil pribadi, serta mengatur preferensi notifikasi                                                                                 | - **users**                                                                                               | Pendaftaran dan manajemen data profil pengguna melalui tabel **users**                                               |
| **Pengguna/Pelanggan**| `/pengguna/booking`                  | Menampilkan jadwal ketersediaan lapangan secara real-time, melakukan booking dengan memilih tanggal, waktu, dan durasi, serta melakukan pembayaran untuk konfirmasi booking              | - **bookings**                                                                                            | Fitur inti aplikasi bagi pengguna untuk melakukan pemesanan lapangan                                                 |
| **Pengguna/Pelanggan**| `/pengguna/riwayat`                  | Menampilkan riwayat booking yang pernah dilakukan, menampilkan detail status, dan mengunduh bukti pembayaran/invoice                                                                 | - **bookings**<br>- **payments**                                                                           | Riwayat transaksi memungkinkan pengguna mengecek booking sebelumnya                                                   |
| **Pengguna/Pelanggan**| `/pengguna/loyalty`                  | Menampilkan jumlah poin yang diperoleh, daftar hadiah yang dapat ditukar, serta riwayat penukaran poin                                                                               | - **user_points**<br>- **loyalty_programs**<br>- **point_redemptions**                                      | Fitur loyalti terintegrasi dengan program poin dan penukaran hadiah                                                    |
| **Pengguna/Pelanggan**| `/pengguna/bantuan`                  | Mengakses panduan penggunaan aplikasi, FAQ tentang booking dan pembayaran, menghubungi customer service, serta memberikan feedback                                                     | *(Tidak langsung tersimpan dalam tabel utama)*<br>~ Bisa dikembangkan dengan tabel FAQ/Feedback jika diperlukan | Fitur bantuan/FAQ biasanya dikelola secara konten atau modul terpisah, sehingga tidak mengharuskan modifikasi pada database |




## Timeline:

| NO | Kegiatan                                                  | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|----|-----------------------------------------------------------|---|----|----|----|----|----|----|
| 1  | Memastikan Teknologi yang digunakan                       | X |    |    |    |    |    |    |
| 2  | Membuat Mockup Awal                                       | X |    |    |    |    |    |    |
| 3  | Membuat Desain Database (ERD dan Fitur Aplikasi)          | X | X  |    |    |    |    |    |
| 4  | Desain/Dokumentasi API dan Endpoint                       | X | X  | X  |    |    |    |    |
| 5  | Pengerjaan UI/UX di Figma                                 | X | X  | X  |    |    |    |    |
| 6  | Pengembangan Backend                                      |   |    | X  | X  | X  | X  |    |
| 7  | Pengembangan Frontend                                     |   |    | X  | X  | X  | X  |    |
| 8  | Pengujian (Testing)                                       |   |    |    |    |    | X  |    |
| 9  | Presentasi                                                |   |    |    |    |    |    | X  |



**Deskripsi**: Desain awal UI aplikasi.
**Link**:
```
https://www.figma.com/design/xEy22akByWa9LvHT4CHZ4G/ProWeb---Mock-up?node-id=0-1&t=NBg7COo7gK9H9btJ-1
```
```
https://www.figma.com/proto/sHIRHBKkCxOVx5wCYpnv7n/Admin-BAS---Mock-Up?node-id=1-2
```








## GitHub Repository
- **Link Backend**: https://github.com/x3naline/balls-backdoor
- **Link Frontend**: https://github.com/wounderfvl/balls-frontdoor
- **Link Devops**: https://github.com/AchmadLyraa/-prowebdevops









