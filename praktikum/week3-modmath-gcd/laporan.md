# Laporan Praktikum Kriptografi
Minggu ke-: 3
Topik: Modular Math (Aritmetika Modular, GCD, Bilangan Prima, Logaritma Diskrit)
Nama: Fausan Dika Kusuma 
NIM: 230202752 
Kelas: 5IKRA  

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
Menyelesaikan operasi aritmetika modular.
Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.

## 2. Dasar Teori
Aritmetika modular adalah tulang punggung (backbone) dari sebagian besar algoritma kriptografi modern, baik kunci simetris maupun kunci publik. Dalam sistem ini, semua operasi dilakukan dalam "ruang" terbatas yang ditentukan oleh modulus $n$. Konsep kunci yang dipelajari adalah Greatest Common Divisor (GCD) yang dihitung menggunakan Algoritma Euclidean untuk menentukan apakah dua bilangan adalah coprime (saling 

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
# --- Langkah 1: Aritmetika Modular ---
def mod_add(a, b, n):
    """Menghitung (a + b) mod n"""
    return (a + b) % n

def mod_sub(a, b, n):
    """Menghitung (a - b) mod n"""
    return (a - b) % n

def mod_mul(a, b, n):
    """Menghitung (a * b) mod n"""
    return (a * b) % n

def mod_exp(base, exp, n):
    """Menghitung (base^exp) mod n (Eksponensiasi Modular)"""
    return pow(base, exp, n)

# --- Langkah 2: GCD & Algoritma Euclidean ---
def gcd(a, b):
    """Menghitung Greatest Common Divisor (GCD) menggunakan Algoritma Euclidean"""
    while b != 0:
        a, b = b, a % b
    return a

# --- Langkah 3: Extended Euclidean Algorithm & Modular Inverse ---
def egcd(a, b):
    """Extended Euclidean Algorithm: Mencari g, x, y sehingga a*x + b*y = g = gcd(a, b)"""
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    x = y1 - (b // a) * x1
    y = x1
    return g, x, y

def modinv(a, n):
    """Menghitung invers modular a^-1 mod n"""
    g, x, _ = egcd(a, n)
    if g != 1:
        return None  # Invers modular tidak ada
    return x % n

# --- Langkah 4: Logaritma Diskrit (Discrete Log) Sederhana ---
def discrete_log(a, b, n):
    """Simulasi sederhana Discrete Log: Mencari x sehingga a^x ≡ b (mod n)"""
    for x in range(n):
        if pow(a, x, n) == b:
            return x
    return None

# --- Contoh Pengujian ---
if __name__ == "__main__":
    print("--- Aritmetika Modular ---")
    print(f"7 + 5 mod 12 = {mod_add(7, 5, 12)}")
    print(f"7 * 5 mod 12 = {mod_mul(7, 5, 12)}")
    print(f"7^128 mod 13 = {mod_exp(7, 128, 13)}")
    print("-" * 30)

    print("--- GCD (Algoritma Euclidean) ---")
    print(f"gcd(54, 24) = {gcd(54, 24)}")
    print("-" * 30)

    print("--- Modular Inverse (Extended Euclidean) ---")
    print(f"Invers 3 mod 11 = {modinv(3, 11)}")
    print(f"Invers 2 mod 4 = {modinv(2, 4)}")
    print("-" * 30)

    print("--- Logaritma Diskrit Sederhana ---")
    print(f"3^x ≡ 4 (mod 7), x = {discrete_log(3, 4, 7)}")
    print("-" * 30)

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
Pertanyaan 1: Apa peran aritmetika modular dalam kriptografi modern?
Aritmetika modular adalah dasar matematis untuk hampir semua sistem kriptografi. Perannya meliputi:
Enkripsi dan Dekripsi: Digunakan dalam operasi inti, seperti eksponensiasi modular dalam RSA atau perkalian matriks modulo $n$ dalam kriptografi kurva eliptik.
Pengurangan Data: Memastikan bahwa hasil operasi pada bilangan yang sangat besar tetap berada dalam batas ukuran kunci yang wajar (modulus $N$), sehingga menjaga efisiensi dan konsistensi data.
Dasar Keamanan: Keamanan algoritma kunci publik didasarkan pada kesulitan komputasi untuk memecahkan masalah matematika yang melibatkan modular, seperti masalah faktorisasi dan masalah logarit

Pertanyaan 2: Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?
Dalam algoritma RSA, kunci dekripsi $d$ harus dihitung sebagai invers modular dari kunci enkripsi $e$ modulo $\phi(N)$, yaitu $e \cdot d \equiv 1 \pmod{\phi(N)}$.
Pentingnya adalah:
Memungkinkan Dekripsi: Kunci $d$ adalah satu-satunya cara untuk membatalkan proses enkripsi. Jika pesan terenkripsi adalah $C \equiv P^e \pmod{N}$, maka proses dekripsi menggunakan $C^d \equiv (P^e)^d \equiv P^{e \cdot d} \equiv P^1 \equiv P \pmod{N}$.
Prasyarat: Keberadaan invers modular $d$ membutuhkan $\text{gcd}(e, \phi(N)) = 1$. Extended Euclidean Algorithm digunakan untuk menghitung $d$ secara deterministik dan efisien.

Pertanyaan 3: Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?
Tantangan utama adalah bahwa tidak ada algoritma efisien yang diketahui yang dapat memecahkan masalah $\text{DL}$ (mencari $x$ dari $a^x \equiv b \pmod{n}$) dalam waktu polinomial jika modulus $n$ sangat besar.
Kompleksitas Komputasi: Metode brute force seperti yang disimulasikan pada praktikum menjadi tidak mungkin. Algoritma terbaik yang ada (seperti Number Field Sieve) memiliki kompleksitas waktu sub-eksponensial.
Dasar Keamanan Kriptografi: Kesulitan memecahkan DL ini menjadi fondasi keamanan bagi algoritma kunci publik seperti Diffie-Hellman Key Exchange dan ElGamal. Ukuran modulus yang besar (misalnya, lebih dari 2048 bit) menjamin bahwa serangan saat ini tidak akan berhasil dalam kerangka waktu yang wajar.

## 8. Kesimpulan
Praktikum ini berhasil mengimplementasikan fungsi-fungsi dasar aritmetika modular, Algoritma Euclidean (GCD), Extended Euclidean Algorithm (Modular Inverse), dan simulasi Logaritma Diskrit sederhana menggunakan Python. Implementasi ini menunjukkan bahwa aritmetika modular adalah landasan yang krusial dalam kriptografi untuk operasi enkripsi/dekripsi dan pembentukan kunci yang aman, di mana sulitnya memecahkan masalah matematika yang berbasis modular (seperti DL) memberikan keamanan yang dibutuhkan.

## 9. Daftar Pustaka
(Stallings, W. Cryptography and Network Security: Principles and Practice. Pearson.
Paar, C., & Pelzl, J. Understanding Cryptography: A Textbook for Students and Practitioners. Springer.
Panduan Modul Praktikum 03: Modular Math (Aritmetika Modular, GCD, Bilangan Prima, Logarit
## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Fausan Dika Kusuma <fauzandikakusuma@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
