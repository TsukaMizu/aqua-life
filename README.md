<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## Dokumentasi Proyek

### ICONIX Process Documentation
- [ICONIX Documentation](docs/ICONIX_DOCUMENTATION.md) – Use Case, Domain Model, Robustness, Sequence, dan Class Diagram
- [SRS – Functional Requirements](docs/srs.md) – Tabel aktor, FR-001 s.d. FR-032, dan NFR
- [Robustness Diagrams (PlantUML)](docs/robustness/) – Satu file `.puml` per FR atau kelompok FR berdekatan:

| File | FR yang Dicakup | Deskripsi |
|------|-----------------|-----------|
| [FR-001-beranda.puml](docs/robustness/FR-001-beranda.puml) | FR-001 | Lihat Halaman Beranda (Guest) |
| [FR-002-003-registrasi.puml](docs/robustness/FR-002-003-registrasi.puml) | FR-002, FR-003 | Registrasi Pengguna (Guest) |
| [FR-004-005-login.puml](docs/robustness/FR-004-005-login.puml) | FR-004, FR-005 | Login & Redirect Berdasarkan Peran |
| [FR-006-logout.puml](docs/robustness/FR-006-logout.puml) | FR-006 | Logout |
| [FR-007-008-hitung-kualitas-air.puml](docs/robustness/FR-007-008-hitung-kualitas-air.puml) | FR-007, FR-008 | Hitung Kualitas Air (Form + WSM) |
| [FR-009-lihat-history.puml](docs/robustness/FR-009-lihat-history.puml) | FR-009 | Lihat Riwayat Penilaian |
| [FR-010-detail-hasil.puml](docs/robustness/FR-010-detail-hasil.puml) | FR-010 | Detail Hasil Penilaian |
| [FR-011-edit-history.puml](docs/robustness/FR-011-edit-history.puml) | FR-011 | Edit Riwayat Penilaian |
| [FR-012-015-kelola-stasiun.puml](docs/robustness/FR-012-015-kelola-stasiun.puml) | FR-012–FR-015 | Kelola Stasiun (CRUD) |
| [FR-016-hasil-penilaian-stasiun.puml](docs/robustness/FR-016-hasil-penilaian-stasiun.puml) | FR-016 | Lihat & Perbarui Hasil Penilaian Stasiun |
| [FR-017-lihat-parameter-bobot.puml](docs/robustness/FR-017-lihat-parameter-bobot.puml) | FR-017 | Lihat Daftar Parameter Bobot WSM |
| [FR-018-019-param-abiotic-utama.puml](docs/robustness/FR-018-019-param-abiotic-utama.puml) | FR-018, FR-019 | Tambah/Perbarui/Hapus Param Abiotik Utama |
| [FR-020-param-abiotic-tambahan.puml](docs/robustness/FR-020-param-abiotic-tambahan.puml) | FR-020 | CRUD Param Abiotik Tambahan |
| [FR-021-param-indeks-biotik.puml](docs/robustness/FR-021-param-indeks-biotik.puml) | FR-021 | CRUD Param Indeks Biotik |
| [FR-022-param-keluarga-biotik.puml](docs/robustness/FR-022-param-keluarga-biotik.puml) | FR-022 | CRUD Param Keluarga Biotik |
| [FR-023-026-kelola-pengguna.puml](docs/robustness/FR-023-026-kelola-pengguna.puml) | FR-023–FR-026 | Kelola Pengguna (CRUD) – Admin |
| [FR-027-pantau-pembayaran.puml](docs/robustness/FR-027-pantau-pembayaran.puml) | FR-027 | Pantau Transaksi Pembayaran – Admin |
| [FR-028-029-pembayaran.puml](docs/robustness/FR-028-029-pembayaran.puml) | FR-028, FR-029 | Halaman & Buat Transaksi Pembayaran (Midtrans) |
| [FR-030-031-kelola-pembayaran-member.puml](docs/robustness/FR-030-031-kelola-pembayaran-member.puml) | FR-030, FR-031 | Perbarui & Hapus Pembayaran (Member) |

---

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[OP.GG](https://op.gg)**
- **[WebReinvent](https://webreinvent.com/?utm_source=laravel&utm_medium=github&utm_campaign=patreon-sponsors)**
- **[Lendio](https://lendio.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
