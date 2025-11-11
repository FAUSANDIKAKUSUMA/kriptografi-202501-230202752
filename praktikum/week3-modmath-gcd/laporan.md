# Laporan Praktikum Kriptografi
Minggu ke-: 3  
Topik: [judul praktikum]  
Nama: Fausan Dika Kusuma 
NIM: 230202752  
Kelas: 5IKRB  

---

## 1. Tujuan
Tujuan pembelajaran praktikum ini adalah mahasiswa diharapkan mampu:
Menyelesaikan operasi aritmetika modular.
Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor)
Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.

---

## 2. Dasar Teori
Aritmetika modular adalah sistem aritmetika untuk bilangan bulat, di mana bilangan 'melingkar' setelah mencapai nilai tertentu yang disebut modulus ($n$). Konsep ini ditulis sebagai $a \equiv b \pmod n$, yang berarti $a$ dan $b$ memiliki sisa yang sama ketika dibagi $n$. Operasi modular, seperti penjumlahan, pengurangan, perkalian, dan eksponensiasi, adalah fundamental dalam banyak algoritma kriptografi, termasuk hash functions dan symmetric key ciphers.Greatest Common Divisor (GCD) atau Faktor Persekutuan Terbesar (FPB) dari dua bilangan bulat $a$ dan $b$ adalah bilangan bulat positif terbesar yang membagi habis $a$ dan $b$. Untuk mencari GCD, digunakan Algoritma Euclidean, yang merupakan metode efisien berdasarkan sifat $\gcd(a, b) = \gcd(b, a \pmod b)$. Algoritma ini kemudian diperluas (Extended Euclidean Algorithm) untuk menemukan invers modular $a^{-1}$ dari $a$ modulo $n$, yaitu bilangan $x$ sedemikian rupa sehingga $ax \equiv 1 \pmod n$, yang hanya ada jika $\gcd(a, n) = 1$. Invers modular sangat krusial untuk operasi dekripsi dalam kriptografi kunci publik.

---

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
# Aritmetika Modular
def mod_add(a, b, n): return (a + b) % n
def mod_sub(a, b, n): return (a - b) % n
def mod_mul(a, b, n): return (a * b) % n
def mod_exp(base, exp, n): return pow(base, exp, n)

def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def egcd(a, b):
    if a == 0:
        return b, 0, 1
    g, x1, y1 = egcd(b % a, a)
    return g, y1 - (b // a) * x1, x1

def modinv(a, n):
    g, x, _ = egcd(a, n)
    if g != 1:
        return None  # Invers tidak ada jika gcd(a, n) != 1
    return x % n

def discrete_log(a, b, n):
    for x in range(1, n):  # x dimulai dari 1
        if pow(a, x, n) == b:
            return x
    return None

# Pengujian
if __name__ == "__main__":
    print("--- Aritmetika Modular ---")
    print("7 + 5 mod 12 =", mod_add(7, 5, 12))
    print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
    print("7^128 mod 13 =", mod_exp(7, 128, 13))

    print("\n--- GCD ---")
    print("gcd(54, 24) =", gcd(54, 24))

    print("\n--- Invers Modular ---")
    print("Invers 3 mod 11 =", modinv(3, 11))

    print("\n--- Logaritma Diskrit ---")
    print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))

# Pengujian
print("--- Aritmetika Modular ---")
print("7 + 5 mod 12 =", mod_add(7, 5, 12))
print("7 * 5 mod 12 =", mod_mul(7, 5, 12))
print("7^128 mod 13 =", mod_exp(7, 128, 13))

print("\n--- GCD ---")
print("gcd(54, 24) =", gcd(54, 24))

print("\n--- Invers Modular ---")
print("Invers 3 mod 11 =", modinv(3, 11))

print("\n--- Logaritma Diskrit ---")
print("3^x ≡ 4 (mod 7), x =", discrete_log(3, 4, 7))

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
1. Apa peran aritmetika modular dalam kriptografi modern?Aritmetika modular adalah landasan matematis dari hampir semua sistem kriptografi modern, terutama yang berbasis kunci publik (asimetris). Perannya meliputi:Keamanan: Operasi modular (terutama eksponensiasi modular) menciptakan fungsi one-way yang mudah dihitung tetapi sulit untuk dibalikkan, menjadikannya dasar bagi masalah sulit seperti Faktorisasi Bilangan Prima (RSA) dan Logaritma Diskrit (Diffie-Hellman/ElGamal), yang menjadi sumber kekuatan keamanan kriptosistem tersebut.Penyederhanaan: Memastikan hasil perhitungan tetap berada dalam rentang tertentu, yang sangat penting saat bekerja dengan bilangan yang sangat besar.Blok Bangunan: Digunakan untuk operasi enkripsi/dekripsi, pembuatan kunci, dan penandatanganan digital.

2. Mengapa invers modular penting dalam algoritma kunci publik (misalnya RSA)?Invers modular sangat penting karena memungkinkan operasi dekripsi.Dalam RSA, kunci dekripsi $d$ adalah invers modular dari kunci enkripsi $e$ modulo $\phi(n)$, yaitu $de \equiv 1 \pmod {\phi(n)}$.Untuk dekripsi, kita membutuhkan operasi yang "membatalkan" operasi enkripsi. Invers modular ini menjamin bahwa saat pesan $c$ dienkripsi dengan $e$ menjadi $c^e \pmod n$, maka mendekripsinya dengan $d$ akan mengembalikan pesan asli: $(c^e)^d \equiv c^{ed} \equiv c^1 \equiv c \pmod n$. Tanpa invers modular, dekripsi tidak mungkin dilakukan.

3. Apa tantangan utama dalam menyelesaikan logaritma diskrit untuk modulus besar?Tantangan utama dalam menyelesaikan Logaritma Diskrit (DL) adalah kompleksitas komputasi yang sangat tinggi (intractable) ketika modulus ($n$) berukuran besar, terutama ketika $n$ adalah bilangan prima besar.Masalah Intractable: Mencari $x$ sedemikian rupa sehingga $a^x \equiv b \pmod n$ secara komputasi sangat sulit. Metode brute-force yang mencoba semua nilai $x$ (seperti yang dilakukan pada langkah percobaan) menjadi tidak praktis karena membutuhkan waktu eksponensial terhadap ukuran $n$.Algoritma Serangan: Algoritma yang lebih canggih seperti Number Field Sieve (NFS) atau Pollard's Rho juga memiliki kompleksitas yang masih terlalu tinggi untuk modulus yang digunakan dalam kriptografi modern (misalnya, 2048-bit atau lebih), sehingga membuat pemecahan DL secara efisien menjadi mustahil dalam rentang waktu yang wajar. Kesulitan inilah yang menjadi dasar keamanan kriptosistem seperti Diffie-Hellman Key Exchange.
---

## 8. Kesimpulan
Implementasi ini menegaskan bahwa operasi modular adalah landasan matematis penting dalam kriptografi untuk menjaga hasil perhitungan tetap terbatas. Selain itu, simulasi sederhana logaritma diskrit menunjukkan kesulitan komputasi mencari eksponen $x$, yang merupakan dasar keamanan bagi banyak skema kriptografi kunci publik.

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit abc12345
Author: Fausan Dika Kusuma <fauzandikakusuma@gmail.com>
Date:   2025-09-20

    week3-modmath: implementasi Caesar Cipher dan laporan )
```
