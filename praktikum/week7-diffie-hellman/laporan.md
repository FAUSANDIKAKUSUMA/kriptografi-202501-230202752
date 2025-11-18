# Laporan Praktikum Kriptografi
Minggu ke-: 7    
Topik: Diffie-Hellman Key Exchange   
Nama: Fausan Dika Kusuma    
NIM: 230202752   
Kelas: 5IKR   

---

## 1. Tujuan
1. Melakukan simulasi protokol Diffie-Hellman untuk pertukaran kunci publik.    
2. Menjelaskan mekanisme pembangkitan kunci bersama menggunakan bilangan prima dan logaritma diskrit.   
3. Menganalisis potensi serangan terhadap Diffie-Hellman, khususnya serangan Man-in-the-Middle (MITM).  

---

## 2. Dasar Teori
Diffie-Hellman Key Exchange adalah protokol kriptografi yang memungkinkan dua pihak bertukar kunci rahasia melalui saluran publik tanpa harus mengirimkan kunci tersebut secara langsung. Protokol ini bekerja menggunakan operasi eksponensial modulo bilangan prima dan mengandalkan kesulitan masalah Discrete Logarithm Problem (DLP), yaitu sulitnya menghitung nilai logaritma diskrit dari suatu bilangan pada modulo tertentu.  

Dalam protokol ini, dua parameter publik digunakan yaitu bilangan prima 𝑝
p dan generator 𝑔 g. Setiap pihak memilih kunci privat secara acak, lalu menghitung kunci publik menggunakan operasi modp dan bertukar kunci publik tersebut. Kunci rahasia bersama diperoleh dari hasil perhitungan kembali menggunakan kunci privat masing-masing.    

Walaupun aman secara matematis, Diffie-Hellman rentan terhadap serangan Man-in-the-Middle, yaitu ketika pihak ketiga mencegat dan mengganti kunci publik sehingga dua pihak yang berkomunikasi tidak menyadari bahwa kunci rahasianya telah diketahui pihak lain. Karena itu, protokol ini biasanya dipadukan dengan autentikasi tambahan.  

---

## 3. Alat dan Bahan
Python 3.11 atau lebih baru  
Visual Studio Code atau editor lain  
Git dan akun GitHub  
Folder praktikum week7-diffie-hellman      
Library standar Python (tanpa library tambahan)  

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code

```python
import random

# parameter umum (disepakati publik)
p = 23  # bilangan prima
g = 5   # generator

# private key masing-masing pihak
a = random.randint(1, p-1)  # secret Alice
b = random.randint(1, p-1)  # secret Bob

# public key
A = pow(g, a, p)
B = pow(g, b, p)

# exchange public key
shared_secret_A = pow(B, a, p)
shared_secret_B = pow(A, b, p)

print("Kunci bersama Alice :", shared_secret_A)
print("Kunci bersama Bob   :", shared_secret_B)

```


---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
1. Mengapa Diffie-Hellman memungkinkan pertukaran kunci di saluran publik?  
Karena kedua pihak hanya bertukar nilai publik hasil operasi eksponensial modulo prima, bukan kunci privat. Nilai publik tersebut tidak dapat digunakan untuk menemukan kunci privat akibat sulitnya menyelesaikan Discrete Logarithm Problem.  

2. Apa kelemahan utama protokol Diffie-Hellman murni?   
Protokol ini tidak memiliki autentikasi, sehingga rawan serangan MITM. Penyerang dapat mengganti public key dan membuat dua kunci berbeda tanpa terdeteksi. 

3. Bagaimana cara mencegah serangan MITM?   
Dengan menambahkan autentikasi seperti sertifikat digital (PKI), tanda tangan digital, atau menggunakan versi yang lebih aman seperti Authenticated Diffie-Hellman (misalnya dalam TLS/SSL).    

---

## 8. Kesimpulan
Pada percobaan ini, protokol Diffie-Hellman berhasil digunakan untuk menghasilkan kunci rahasia bersama. Namun, simulasi MITM membuktikan bahwa Diffie-Hellman tanpa autentikasi sangat rentan disusupi. Oleh karena itu, mekanisme autentikasi wajib digunakan untuk menjaga keamanan komunikasi.  

---

## 9. Daftar Pustaka
Paar, C., & Pelzl, J. (2010). Understanding Cryptography: A Textbook for Students and Practitioners. Springer.  

Menezes, A. J., van Oorschot, P., & Vanstone, S. (1996). Handbook of Applied Cryptography. CRC Press.   

Boneh, D. (1999). The Decision Diffie–Hellman Problem. Algorithmic Number Theory Symposium (ANTS).  

---

## 10. Commit Log
commit 57299de72959e169d30532f43ebbacf177eadf28     
Author: FAUSANDIKAKUSUMA <fauzandikakusuma@gmail.com>   
Date:   Tue Nov 18 12:41:57 2025 +0700  

    week7-diffie-hellman
    week7-cryptosystem: implementasi Caesar Cipher dan laporan 
```
