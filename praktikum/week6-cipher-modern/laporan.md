# Laporan Praktikum Kriptografi
Minggu ke-: 6   
Topik: Cipher Modern (DES, AES, RSA)    
Nama: Fausan Dika Kusuma     
NIM: 230202752   
Kelas: 5IKRB    

---

## 1. Tujuan
Tujuan praktikum minggu ke-6 adalah:

1. Mengimplementasikan algoritma cipher modern, yaitu DES, AES-128, dan RSA menggunakan bahasa Python.  
2. Menguji proses enkripsi dan dekripsi pada masing-masing algoritma untuk memahami cara kerja cipher modern.   
3. enjelaskan perbedaan konsep symmetric key (DES & AES) dan asymmetric key (RSA).  
4. Melakukan dokumentasi hasil praktikum dalam bentuk laporan dan commit Git.
---

## 2. Dasar Teori
Cipher modern adalah algoritma kriptografi yang digunakan pada sistem keamanan digital saat ini. Cipher modern terbagi menjadi dua kategori utama: cipher simetris dan cipher asimetris. Cipher simetris menggunakan satu kunci yang sama untuk enkripsi dan dekripsi, contohnya DES dan AES. Cipher asimetris menggunakan pasangan kunci publik dan privat, seperti pada algoritma RSA.    

DES (Data Encryption Standard) adalah algoritma blok cipher 64-bit dengan kunci efektif 56 bit. DES kini dianggap tidak aman karena ukuran kuncinya kecil dan rentan brute-force. AES (Advanced Encryption Standard) adalah pengganti DES, bekerja dengan ukuran blok 128 bit dan mendukung panjang kunci 128/192/256 bit. AES lebih aman dan efisien sehingga menjadi standar enkripsi modern. 

RSA adalah algoritma kriptografi kunci publik yang bekerja berdasarkan sifat matematika bilangan prima besar dan modulo eksponensial. RSA menggunakan pasangan kunci: kunci publik untuk enkripsi dan kunci privat untuk dekripsi, sehingga cocok untuk digital signature dan secure key exchange.

---

## 3. Alat dan Bahan
Python 3.11
Visual Studio Code
Library tambahan:
pycryptodome
Git & GitHub

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
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128 bit key
cipher = AES.new(key, AES.MODE_EAX)

plaintext = b"Modern Cipher AES Example"
ciphertext, tag = cipher.encrypt_and_digest(plaintext)

print("Ciphertext:", ciphertext)
cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
decrypted = cipher_dec.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Enkripsi dengan public key
cipher_rsa = PKCS1_OAEP.new(public_key)
plaintext = b"RSA Example"
ciphertext = cipher_rsa.encrypt(plaintext)
print("Ciphertext:", ciphertext)

# Dekripsi dengan private key
decipher_rsa = PKCS1_OAEP.new(private_key)
decrypted = decipher_rsa.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())
```
)

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
(Jawab pertanyaan diskusi yang diberikan pada modul.  
1. Perbedaan mendasar antara DES, AES, dan RSA dalam hal kunci dan keamanan
DES: cipher simetris, kunci 56 bit, sudah tidak aman terhadap brute-force.
AES: cipher simetris, kunci 128/192/256 bit, aman dan menjadi standar modern.
RSA: cipher asimetris menggunakan pasangan kunci (publik & privat); keamanan bergantung pada sulitnya faktorisasi bilangan prima besar. 

2. Mengapa AES lebih banyak digunakan dibanding DES?
AES jauh lebih aman karena ukuran kuncinya besar (128 bit atau lebih), lebih efisien, lebih cepat, dan tidak rentan brute-force. DES sudah dinyatakan tidak aman sejak tahun 2000 karena kunci 56-bit terlalu kecil.    

3. Mengapa RSA dikategorikan sebagai algoritma asimetris, dan bagaimana proses pembangkitan kuncinya?
RSA disebut asimetris karena menggunakan dua kunci berbeda:
Public key untuk enkripsi
Private key untuk dekripsi
Kunci dibangkitkan dengan:
Memilih dua bilangan prima besar p dan q.
Menghitung n = p × q.
Menghitung φ(n) = (p−1)(q−1).
Memilih e sebagai eksponen publik.
Menghitung d sebagai invers modular dari e terhadap φ(n).
)
---

## 8. Kesimpulan
Pada praktikum ini berhasil diimplementasikan algoritma cipher modern DES, AES, dan RSA menggunakan Python. Hasil uji menunjukkan bahwa proses enkripsi dan dekripsi berjalan sesuai teori. Praktikum ini membantu memahami perbedaan cipher simetris dan asimetris serta penerapannya dalam keamanan modern.   

---

## 9. Daftar Pustaka
Stallings, W. Cryptography and Network Security, 7th Edition.
Katz, J., & Lindell, Y. Introduction to Modern Cryptography.
Documentation PyCryptodome Library.

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
