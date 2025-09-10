# Login Admin

## 1. Informasi Target

* **Nama Aplikasi** : OWASP Juice Shop
* **URL** : `http://localhost:3000`
* **Lingkungan** : Localhost (uji coba di mesin sendiri)
* **Tujuan Uji** : Menguji keamanan autentikasi login

---

## 2. Tahap Reconnaissance

* Saat membuka aplikasi di `http://localhost:3000/#/`, terlihat halaman utama berisi daftar produk.
* Menu **Account** di pojok kanan atas memiliki opsi **Login**.
* Dari sini diketahui ada fitur autentikasi user.

  ![WhatsApp Image 2025-09-06 at 22 34 07_120e67a9](https://github.com/user-attachments/assets/8ebe89d6-4195-4336-b732-4712f0ac5546)

---

## 3. Tahap Akses Login

* Masuk ke halaman login di `http://localhost:3000/#/login`.
* Tersedia field untuk **Email** dan **Password**.
* Dari dokumentasi OWASP Juice Shop maupun pengalaman pentest, diketahui aplikasi ini sering mengandung **default credentials**.

  ![WhatsApp Image 2025-09-06 at 22 34 56_7283f1b8](https://github.com/user-attachments/assets/9d2f6ed4-0a00-4a53-914a-b3516b91a017)


---

## 4. Eksploitasi (Default Credentials)

* Mencoba login dengan kredensial berikut:

```
Email    : admin@juice-sh.op
Password : admin123
```

* Tekan tombol **Log in**.

📌 Hasil: Berhasil login sebagai **Admin**.

---

## 5. Analisis Kerentanan

Kerentanan ini muncul karena:

* Aplikasi masih menggunakan **default credentials** yang lemah.
* Tidak ada peringatan atau kebijakan keamanan untuk mengganti password default.

---

## 6. Dampak

Jika ini terjadi pada aplikasi nyata, risikonya:

* **Kebocoran Data**: Penyerang bisa mengakses data pelanggan, transaksi, dan informasi sensitif lainnya.
* **Pengambilalihan Sistem**: Penyerang dengan hak admin bisa mengubah produk, harga, bahkan menanam backdoor.
* **Kredibilitas Hilang**: Keamanan aplikasi dipertanyakan jika default password tidak dihapus.

---

## 7. Rekomendasi Perbaikan

* **Disable default credentials** sebelum aplikasi dipublikasikan.
* Terapkan **password policy** (panjang minimal, kombinasi karakter, dsb).
* Gunakan **multi-factor authentication (MFA)** untuk akun penting.
* Terapkan **rate limiting / account lockout** untuk mencegah brute force.
* Audit rutin untuk memastikan tidak ada akun default yang masih aktif.

---
