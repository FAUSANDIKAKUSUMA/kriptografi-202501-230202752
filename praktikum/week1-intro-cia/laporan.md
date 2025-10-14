# Laporan Praktikum Kriptografi

    Minggu ke-: 1
    Topik: Sejarah Kriptografi & Prinsip CIA
    Nama: Fausan Dika Kusuma
    NIM: 230202752
    Kelas: 5IKRB

---

## 1. Tujuan

Menjelaskan sejarah dan evolusi kriptografi dari masa klasik hingga modern.
Menyebutkan prinsip Confidentiality, Integrity, Availability (CIA) dengan benar.
Menyimpulkan peran kriptografi dalam sistem keamanan informasi modern.
Menyiapkan repositori GitHub sebagai media kerja praktikum.

---

## 2. Dasar Teori

Ringkasan Era Kriptografi Klasik (Cipher)
Era kriptografi klasik merupakan masa awal perkembangan kriptografi yang berfokus pada teknik penyandian pesan menggunakan metode sederhana berbasis substitusi dan transposisi huruf. Tujuan utamanya adalah menyembunyikan isi pesan agar hanya pihak yang mengetahui kunci dapat membacanya.
Beberapa metode terkenal dalam era ini antara lain:
Caesar Cipher, yang menggantikan setiap huruf dengan huruf lain yang berjarak tetap dalam alfabet.
Vigenère Cipher, yang menggunakan kata kunci untuk menentukan pergeseran huruf, sehingga lebih sulit dipecahkan.
Playfair Cipher, yang menyandikan pasangan huruf sekaligus untuk meningkatkan keamanan.
Kriptografi klasik umumnya hanya mengandalkan manipulasi huruf dan simbol tanpa melibatkan matematika kompleks. Namun, dengan kemajuan teknologi dan kemampuan komputasi, cipher klasik menjadi mudah dipecahkan menggunakan analisis frekuensi. Meskipun demikian, era ini menjadi fondasi penting bagi perkembangan kriptografi modern.
Perkembangan Kriptografi Modern (RSA)
Kriptografi modern muncul seiring kemajuan komputer dan matematika, ditandai dengan penggunaan algoritma berbasis kunci publik dan privat. Salah satu algoritma paling berpengaruh adalah RSA (Rivest–Shamir–Adleman) yang ditemukan pada tahun 1977. RSA menggunakan prinsip faktorisasi bilangan prima besar untuk mengenkripsi dan mendekripsi pesan. Sistem ini memungkinkan komunikasi aman tanpa perlu bertukar kunci rahasia secara langsung. Kriptografi modern juga mendukung keamanan digital seperti tanda tangan digital, enkripsi data, dan sertifikat digital.
Evolusi Menuju Kriptografi Kontemporer (Cryptocurrency)
Era kriptografi kontemporer ditandai dengan penerapan kriptografi dalam teknologi blockchain dan cryptocurrency seperti Bitcoin dan Ethereum. Sistem ini memanfaatkan algoritma hashing (SHA-256), tanda tangan digital, dan kriptografi asimetris untuk menjamin keamanan transaksi, integritas data, serta otentikasi pengguna tanpa memerlukan otoritas pusat. Kriptografi dalam cryptocurrency berperan penting untuk membangun kepercayaan terdistribusi dan transparansi, menjadikannya fondasi utama bagi sistem keuangan digital masa kini.

---

## 3. Alat dan Bahan

(- Python 3.x

- Visual Studio Code / editor lain
- Git dan akun GitHub
- Library tambahan (misalnya pycryptodome, jika diperlukan) )

---

## 4. Langkah Percobaan

(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:

1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code

(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def encrypt(text, key):
    return ...
```

)

---

## 6. Hasil dan Pembahasan

(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).

- Berikan tabel atau ringkasan hasil uji jika diperlukan.
- Jelaskan apakah hasil sesuai ekspektasi.
- Bahas error (jika ada) dan solusinya.

Hasil Repo:

![Hasil Repo](screenshots/sekrinsut.png)
)

---

## 7. Jawaban Pertanyaan

(Jawab pertanyaan diskusi yang diberikan pada modul.

- Pertanyaan 1: Tokoh yang sering dianggap sebagai bapak kriptografi modern adalah Whitfield Diffie dan Martin Hellman.
  Mereka memperkenalkan konsep kriptografi kunci publik (public-key cryptography) pada tahun 1976 melalui makalah berjudul “New Directions in Cryptography”.
  Penemuan ini menjadi dasar bagi sistem keamanan digital modern seperti SSL, PGP, dan berbagai sistem enkripsi di internet.
- Pertanyaan 2:
  RSA (Rivest–Shamir–Adleman)\*\*
  Digunakan untuk enkripsi dan tanda tangan digital.
  ECC (Elliptic Curve Cryptography)
  Lebih efisien daripada RSA dengan ukuran kunci yang lebih kecil.
  Diffie–Hellman Key Exchange
  Digunakan untuk pertukaran kunci rahasia secara aman.
  ElGamal
  Sering digunakan untuk enkripsi dan sistem tanda tangan digital.
  -Pertanyaan 3:
  Perbedaan utama antara kriptografi klasik dan kriptografi modern terletak pada metode enkripsi, jenis kunci, dan dasar keamanannya.
  Kriptografi klasik menggunakan satu kunci yang sama untuk proses enkripsi dan dekripsi (bersifat simetris). Metode yang digunakan biasanya berupa substitusi atau transposisi huruf pada teks alfabet. Keamanan sistem klasik ini relatif lemah karena dapat dipecahkan melalui analisis frekuensi atau percobaan manual.
  Sementara itu, kriptografi modern menggunakan dua kunci yang berbeda, yaitu kunci publik dan kunci privat (bersifat asimetris). Sistem ini didasarkan pada teori matematika yang kompleks seperti faktorisasi bilangan prima, logaritma diskret, dan kurva eliptik. Kriptografi modern lebih aman dan digunakan untuk melindungi data digital dalam komunikasi dan transaksi elektronik di era teknologi saat ini.
  )

---

## 8. Kesimpulan

(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan. )

---

## 9. Daftar Pustaka

(Cantumkan referensi yang digunakan.  
Contoh:

- Katz, J., & Lindell, Y. _Introduction to Modern Cryptography_.
- Stallings, W. _Cryptography and Network Security_. )

---

## 10. Commit Log

(Tuliskan bukti commit Git yang relevan.  
Contoh:

```
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
