# Dokumen Analisis Kebutuhan – Aqua Life

> **Proyek:** Aqua Life – Sistem Penilaian Kualitas Air  
> **Arsitektur:** Laravel 10 + Inertia.js (MVC)  
> **Tanggal:** 2026-05-04  
> **Versi:** 1.0

---

## 1. Tabel Aktor

| No | Aktor          | Deskripsi                                                                                                                              |
|----|----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **Guest**      | Pengguna yang belum terautentikasi. Dapat mengakses halaman beranda, mendaftar akun baru, dan masuk ke sistem.                         |
| 2  | **Member**     | Pengguna terdaftar dengan peran *member*. Dapat melakukan perhitungan kualitas air, melihat riwayat penilaian, dan mengelola pembayaran langganan. |
| 3  | **Operator**   | Pengguna terdaftar dengan peran *operator*. Dapat mengelola stasiun pengamatan, bobot parameter, dan melakukan perhitungan kualitas air. |
| 4  | **Admin**      | Pengguna dengan hak akses tertinggi. Mengelola seluruh data pengguna, stasiun, bobot parameter, riwayat penilaian, dan memantau pembayaran. |
| 5  | **Midtrans**   | Sistem pembayaran eksternal (payment gateway). Mengirimkan notifikasi webhook setelah transaksi pembayaran Member diproses.             |

---

## 2. Tabel SRS

### 2.1 Functional Requirements (FR)

| NO | SRS-ID  | Deskripsi                                                                                                                                          | Aktor                    |
|----|---------|----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| 1  | FR-001  | Sistem menampilkan halaman beranda bagi pengguna yang belum login.                                                                                 | Guest                    |
| 2  | FR-002  | Sistem menyediakan formulir pendaftaran akun baru (*registrasi*).                                                                                  | Guest                    |
| 3  | FR-003  | Sistem memproses data pendaftaran dan membuat akun pengguna baru dengan peran default *member*.                                                    | Guest                    |
| 4  | FR-004  | Sistem menyediakan formulir login dan mengautentikasi pengguna berdasarkan kredensial (email & kata sandi).                                        | Guest                    |
| 5  | FR-005  | Sistem mengarahkan pengguna yang telah login ke halaman sesuai peran (*member*, *operator*, atau *admin*).                                         | Member, Operator, Admin  |
| 6  | FR-006  | Sistem memproses logout dan mengakhiri sesi pengguna yang sedang aktif.                                                                            | Member, Operator, Admin  |
| 7  | FR-007  | Sistem menampilkan formulir perhitungan kualitas air yang memuat parameter abiotik utama, abiotik tambahan, dan indeks biotik.                     | Member, Operator, Admin  |
| 8  | FR-008  | Sistem menghitung skor kualitas air menggunakan algoritma WSM (*Weighted Sum Model*) berdasarkan parameter yang dimasukkan, lalu menyimpan hasilnya.| Member, Operator, Admin  |
| 9  | FR-009  | Sistem menampilkan daftar riwayat penilaian kualitas air milik pengguna yang sedang login.                                                         | Member, Operator, Admin  |
| 10 | FR-010  | Sistem menampilkan halaman detail hasil penilaian kualitas air berdasarkan ID riwayat.                                                             | Member, Operator, Admin  |
| 11 | FR-011  | Sistem memungkinkan pengguna mengedit data input dari riwayat penilaian yang sudah ada dan menyimpan pembaruan hasilnya.                           | Member, Operator, Admin  |
| 12 | FR-012  | Sistem menampilkan daftar stasiun pengamatan yang terdaftar beserta informasinya.                                                                  | Operator, Admin          |
| 13 | FR-013  | Sistem memungkinkan penambahan stasiun pengamatan baru (nama, lokasi, zona geografis, tipe air, dsb.).                                             | Operator, Admin          |
| 14 | FR-014  | Sistem memungkinkan pembaruan data stasiun pengamatan yang sudah ada.                                                                              | Operator, Admin          |
| 15 | FR-015  | Sistem memungkinkan penghapusan stasiun pengamatan.                                                                                                | Operator, Admin          |
| 16 | FR-016  | Sistem menampilkan halaman hasil penilaian terakhir dari suatu stasiun dan memungkinkan pembaruan data riwayat stasiun tersebut.                   | Operator, Admin          |
| 17 | FR-017  | Sistem menampilkan daftar parameter bobot (abiotik utama, abiotik tambahan, indeks biotik, dan keluarga biotik) yang digunakan dalam WSM.          | Operator, Admin          |
| 18 | FR-018  | Sistem memungkinkan penambahan parameter bobot abiotik utama beserta nilai bobotnya.                                                               | Operator, Admin          |
| 19 | FR-019  | Sistem memungkinkan pembaruan dan penghapusan parameter bobot abiotik utama.                                                                       | Operator, Admin          |
| 20 | FR-020  | Sistem memungkinkan penambahan, pembaruan, dan penghapusan parameter bobot abiotik tambahan.                                                       | Operator, Admin          |
| 21 | FR-021  | Sistem memungkinkan penambahan, pembaruan, dan penghapusan parameter indeks biotik.                                                                | Operator, Admin          |
| 22 | FR-022  | Sistem memungkinkan penambahan, pembaruan, dan penghapusan parameter keluarga biotik.                                                              | Operator, Admin          |
| 23 | FR-023  | Sistem menampilkan daftar seluruh pengguna terdaftar beserta peran dan statusnya.                                                                  | Admin                    |
| 24 | FR-024  | Sistem memungkinkan Admin membuat akun pengguna baru secara langsung (dengan peran yang dapat ditentukan).                                         | Admin                    |
| 25 | FR-025  | Sistem memungkinkan Admin memperbarui data dan peran pengguna yang sudah ada.                                                                      | Admin                    |
| 26 | FR-026  | Sistem memungkinkan Admin menghapus akun pengguna.                                                                                                 | Admin                    |
| 27 | FR-027  | Sistem menampilkan daftar transaksi pembayaran dari seluruh Member untuk dipantau Admin.                                                           | Admin                    |
| 28 | FR-028  | Sistem menampilkan halaman pembayaran bagi Member untuk berlangganan atau memperpanjang akses.                                                     | Member                   |
| 29 | FR-029  | Sistem membuat transaksi pembayaran baru dan mengintegrasikan proses pembayaran dengan Midtrans (menghasilkan token pembayaran).                   | Member                   |
| 30 | FR-030  | Sistem memungkinkan Member memperbarui status pembayaran secara manual (misalnya membatalkan sebelum diproses).                                    | Member                   |
| 31 | FR-031  | Sistem memungkinkan Member menghapus data pembayaran yang belum selesai.                                                                           | Member                   |
| 32 | FR-032  | Sistem menerima notifikasi webhook dari Midtrans dan memperbarui status pembayaran Member secara otomatis berdasarkan hasil transaksi.             | Midtrans                 |

### 2.2 Non-Functional Requirements (NFR)

| NO | SRS-ID  | Deskripsi                                                                                                                                        | Aktor                         |
|----|---------|--------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| 1  | NFR-001 | Sistem mengimplementasikan autentikasi berbasis sesi (Laravel Session) sehingga halaman berproteksi hanya dapat diakses oleh pengguna yang login. | Member, Operator, Admin       |
| 2  | NFR-002 | Sistem menerapkan kontrol akses berbasis peran (*Role-Based Access Control*): setiap peran hanya dapat mengakses rute yang diizinkan.             | Member, Operator, Admin       |
| 3  | NFR-003 | Sistem melindungi semua permintaan *state-changing* (POST/PUT/DELETE) dengan token CSRF Laravel.                                                  | Member, Operator, Admin       |
| 4  | NFR-004 | Sistem menggunakan HTTPS untuk memastikan kerahasiaan data yang dikirimkan antara klien dan server.                                               | Guest, Member, Operator, Admin, Midtrans |
| 5  | NFR-005 | Antarmuka pengguna dibangun dengan Inertia.js + Vue/React sehingga navigasi antar halaman berlangsung tanpa *full page reload* (SPA-like).        | Guest, Member, Operator, Admin |
| 6  | NFR-006 | Webhook Midtrans diekspos melalui rute publik (`/api/midtrans/webhook`) tanpa middleware autentikasi sesi agar dapat diakses oleh server Midtrans.| Midtrans                      |
| 7  | NFR-007 | Sistem harus dapat menangani kegagalan pembayaran dari Midtrans secara *graceful* (status transaksi diperbarui sesuai respons webhook).           | Midtrans                      |
| 8  | NFR-008 | Kata sandi pengguna disimpan dalam bentuk *hash* menggunakan algoritma bcrypt bawaan Laravel.                                                     | Guest, Member, Operator, Admin |
| 9  | NFR-009 | Seluruh validasi input formulir (pendaftaran, login, parameter kualitas air, dll.) dilakukan di sisi server sebelum data disimpan ke basis data.  | Guest, Member, Operator, Admin |
| 10 | NFR-010 | Sistem harus dapat merespons permintaan halaman umum dalam waktu kurang dari 2 detik pada kondisi beban normal.                                   | Guest, Member, Operator, Admin |

---

## 3. Asumsi dan Catatan

1. **Peran default Member saat registrasi**: Berdasarkan kode `AuthController`, pengguna yang mendaftar secara mandiri mendapatkan peran *member*. Peran *operator* dan *admin* hanya dapat ditetapkan oleh Admin melalui halaman *Kelola Pengguna*.
2. **Algoritma WSM**: Fitur "Hitung Kualitas Air" menggunakan *Weighted Sum Model* yang menggabungkan parameter abiotik dan biotik. Detail bobot dikelola melalui fitur *Kelola Bobot*.
3. **Zona geografis dan tipe air**: Model `GeoZone` dan `WaterType` ada di *codebase* dan digunakan dalam data stasiun, namun tidak memiliki rute CRUD tersendiri yang terekspos – dianggap diinisialisasi melalui *database seeder/migration*.
4. **NFR-004 – HTTPS**: Tidak dapat diverifikasi langsung dari *source code*; diasumsikan diterapkan pada tahap deployment/konfigurasi server.
5. **NFR-010 – Performa**: Target waktu respons kurang dari 2 detik adalah standar umum yang diasumsikan diterapkan pada konfigurasi server produksi.
5. **Notifikasi alert kualitas air**: Tidak ditemukan `AlertService` atau mekanisme notifikasi otomatis (email/SMS) di *codebase* saat ini. FR hanya mencakup fitur yang terkonfirmasi ada.
