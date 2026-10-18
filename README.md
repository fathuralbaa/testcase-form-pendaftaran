# Test Case Form Pendaftaran Online (Soal 7)

Black-box testing menggunakan Equivalence Partitioning (EP) dan Boundary Value Analysis (BVA).
Tanggal acuan pengujian: 2026-10-19.

## Spesifikasi

| Field | Validasi |
|---|---|
| Nama | 3-100 karakter |
| Email | Format email valid |
| No. HP | 10-13 digit, diawali 08 |
| Tanggal Lahir | Format YYYY-MM-DD, umur minimal 17 tahun |
| Password | Minimal 8 karakter, huruf besar, huruf kecil, angka, simbol |
| Konfirmasi Password | Harus sama dengan password |

## 1. Equivalence Partitioning

| Field | Partisi | Kategori | Kondisi |
|---|---|---|---|
| Nama | P1 | Valid | 3-100 karakter |
| Nama | P2 | Invalid | < 3 karakter |
| Nama | P3 | Invalid | > 100 karakter |
| Nama | P4 | Invalid | Kosong |
| Email | P1 | Valid | Format email valid |
| Email | P2 | Invalid | Tanpa @ |
| Email | P3 | Invalid | Tanpa domain |
| Email | P4 | Invalid | Kosong |
| No. HP | P1 | Valid | 10-13 digit, diawali 08 |
| No. HP | P2 | Invalid | < 10 digit |
| No. HP | P3 | Invalid | > 13 digit |
| No. HP | P4 | Invalid | Tidak diawali 08 |
| No. HP | P5 | Invalid | Mengandung non-digit |
| Tanggal Lahir | P1 | Valid | Format YYYY-MM-DD, umur >= 17 tahun |
| Tanggal Lahir | P2 | Invalid | Format valid, umur < 17 tahun |
| Tanggal Lahir | P3 | Invalid | Format salah (mis. DD-MM-YYYY) |
| Tanggal Lahir | P4 | Invalid | Tanggal tidak ada / di masa depan |
| Tanggal Lahir | P5 | Invalid | Kosong |
| Password | P1 | Valid | >= 8 karakter, huruf besar, kecil, angka, simbol |
| Password | P2 | Invalid | < 8 karakter |
| Password | P3 | Invalid | Tanpa huruf besar |
| Password | P4 | Invalid | Tanpa huruf kecil |
| Password | P5 | Invalid | Tanpa angka |
| Password | P6 | Invalid | Tanpa simbol |
| Konfirmasi Password | P1 | Valid | Sama persis dengan password |
| Konfirmasi Password | P2 | Invalid | Berbeda dengan password |
| Konfirmasi Password | P3 | Invalid | Kosong |

## 2. Boundary Value Analysis

| Field | Boundary | Nilai | Kategori | Expected Output |
|---|---|---|---|---|
| Nama (panjang) | min-1 | 2 | Invalid | Ditolak, nama minimal 3 karakter |
| Nama (panjang) | min | 3 | Valid | Diterima (valid) |
| Nama (panjang) | min+1 | 4 | Valid | Diterima (valid) |
| Nama (panjang) | max-1 | 99 | Valid | Diterima (valid) |
| Nama (panjang) | max | 100 | Valid | Diterima (valid) |
| Nama (panjang) | max+1 | 101 | Invalid | Ditolak, nama maksimal 100 karakter |
| No. HP (jumlah digit) | min-1 | 9 | Invalid | Ditolak, minimal 10 digit |
| No. HP (jumlah digit) | min | 10 | Valid | Diterima (valid) |
| No. HP (jumlah digit) | min+1 | 11 | Valid | Diterima (valid) |
| No. HP (jumlah digit) | max-1 | 12 | Valid | Diterima (valid) |
| No. HP (jumlah digit) | max | 13 | Valid | Diterima (valid) |
| No. HP (jumlah digit) | max+1 | 14 | Invalid | Ditolak, maksimal 13 digit |
| Tanggal Lahir (umur) | min-1 | 2009-10-20 (16 th 364 hari) | Invalid | Ditolak, umur minimal 17 tahun |
| Tanggal Lahir (umur) | min | 2009-10-19 (tepat 17 th) | Valid | Diterima (valid) |
| Tanggal Lahir (umur) | min+1 | 2009-10-18 (17 th 1 hari) | Valid | Diterima (valid) |
| Password (panjang) | min-1 | 7 | Invalid | Ditolak, password minimal 8 karakter |
| Password (panjang) | min | 8 | Valid | Diterima (valid) |
| Password (panjang) | min+1 | 9 | Valid | Diterima (valid) |

## 3. Test Case (32 test case)

| ID | Field | Teknik | Input | Expected Output |
|---|---|---|---|---|
| TC-7.01 | Semua field | EP (valid) | Nama "Siti Aminah", Email "siti@mail.com", HP "081234567890", Lahir "2000-05-17", Password "Passw0rd!", Konfirmasi "Passw0rd!" | Pendaftaran berhasil |
| TC-7.02 | Nama | EP | "" (kosong) | Ditolak, nama wajib diisi |
| TC-7.03 | Nama | BVA min-1 | "Al" (2 karakter) | Ditolak, nama minimal 3 karakter |
| TC-7.04 | Nama | BVA min | "Ali" (3 karakter) | Diterima (valid) |
| TC-7.05 | Nama | BVA max | "A" x 100 karakter | Diterima (valid) |
| TC-7.06 | Nama | BVA max+1 | "A" x 101 karakter | Ditolak, nama maksimal 100 karakter |
| TC-7.07 | Email | EP | "siti.aminah@mail.co.id" | Diterima (valid) |
| TC-7.08 | Email | EP | "siti.mail.com" (tanpa @) | Ditolak, format email tidak valid |
| TC-7.09 | Email | EP | "siti@" (tanpa domain) | Ditolak, format email tidak valid |
| TC-7.10 | Email | EP | "" (kosong) | Ditolak, email wajib diisi |
| TC-7.11 | No. HP | BVA min-1 | "081234567" (9 digit) | Ditolak, minimal 10 digit |
| TC-7.12 | No. HP | BVA min | "0812345678" (10 digit) | Diterima (valid) |
| TC-7.13 | No. HP | BVA max | "0812345678901" (13 digit) | Diterima (valid) |
| TC-7.14 | No. HP | BVA max+1 | "08123456789012" (14 digit) | Ditolak, maksimal 13 digit |
| TC-7.15 | No. HP | EP | "0712345678901" (tidak diawali 08) | Ditolak, nomor harus diawali 08 |
| TC-7.16 | No. HP | EP | "08123abc7890" (ada huruf) | Ditolak, hanya boleh digit |
| TC-7.17 | Tgl Lahir | EP | "2000-05-17" | Diterima (valid) |
| TC-7.18 | Tgl Lahir | BVA min | "2009-10-19" (tepat 17 tahun; tanggal uji 2026-10-19) | Diterima (valid) |
| TC-7.19 | Tgl Lahir | BVA min-1 | "2009-10-20" (16 tahun 364 hari) | Ditolak, umur minimal 17 tahun |
| TC-7.20 | Tgl Lahir | EP | "19-10-2009" (format salah) | Ditolak, format harus YYYY-MM-DD |
| TC-7.21 | Tgl Lahir | EP | "2000-02-30" (tanggal tidak ada) | Ditolak, tanggal tidak valid |
| TC-7.22 | Tgl Lahir | EP | "2030-01-01" (masa depan) | Ditolak, tanggal lahir tidak valid |
| TC-7.23 | Tgl Lahir | EP | "" (kosong) | Ditolak, tanggal lahir wajib diisi |
| TC-7.24 | Password | BVA min | "Pass0rd!" (8 karakter) | Diterima (valid) |
| TC-7.25 | Password | BVA min-1 | "Pas0rd!" (7 karakter) | Ditolak, password minimal 8 karakter |
| TC-7.26 | Password | EP | "Password1" (tanpa simbol) | Ditolak, wajib ada simbol |
| TC-7.27 | Password | EP | "password1!" (tanpa huruf besar) | Ditolak, wajib ada huruf besar |
| TC-7.28 | Password | EP | "PASSWORD1!" (tanpa huruf kecil) | Ditolak, wajib ada huruf kecil |
| TC-7.29 | Password | EP | "Password!" (tanpa angka) | Ditolak, wajib ada angka |
| TC-7.30 | Konfirmasi | EP | Password "Passw0rd!", Konfirmasi "Passw0rd!" | Diterima (valid) |
| TC-7.31 | Konfirmasi | EP | Password "Passw0rd!", Konfirmasi "Passw0rd?" | Ditolak, konfirmasi password tidak sama |
| TC-7.32 | Konfirmasi | EP | Password "Passw0rd!", Konfirmasi "" (kosong) | Ditolak, konfirmasi password wajib diisi |
