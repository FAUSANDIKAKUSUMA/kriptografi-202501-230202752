# Laporan Praktikum Kriptografi
Minggu ke-: 4 
Topik: Entropy & Unicity Distance (Evaluasi Kekuatan Kunci dan Brute Force) 
Nama: Fausan Dika Kusuma  
NIM: 230202752  
Kelas: 5IKRB  

---

## 1. Tujuan
Tujuan pembelajaran praktikum ini adalah mahasiswa diharapkan mampu:
Menyelesaikan operasi aritmetika modular.
Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).
Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.
---

## 2. Dasar Teori
Konsep utama dalam mengevaluasi kekuatan suatu sistem kriptografi adalah Entropi Kunci dan Unicity Distance. Entropi Kunci adalah ukuran yang digunakan untuk menilai ketidakpastian atau keacakan dari kunci yang digunakan. Nilai entropi yang tinggi menunjukkan bahwa ruang kunci (keyspace), yaitu semua kemungkinan kombinasi kunci, berukuran sangat besar dan tidak terstruktur. Secara sederhana, semakin tinggi entropinya, semakin banyak upaya yang dibutuhkan penyerang untuk mencoba setiap kunci yang mungkin dalam serangan brute force, sehingga membuat kunci tersebut lebih kuat. Kriptosistem modern seperti AES sengaja dirancang dengan entropi kunci yang sangat tinggi (misalnya 128 bit) agar tidak mungkin dipecahkan dengan cara brute force dalam jangka waktu yang realistis.

Konsep kedua, Unicity Distance, berkaitan dengan hubungan antara keamanan sandi dan redundansi bahasa yang digunakan dalam plaintext (teks asli). Redundansi bahasa mengacu pada pola dan ketergantungan yang melekat dalam suatu bahasa, seperti frekuensi huruf (misalnya 'E' paling sering muncul) atau urutan kata tertentu. Unicity Distance adalah panjang minimum ciphertext (teks sandi) yang dibutuhkan agar pola bahasa ini cukup terungkap sehingga hanya tersisa satu kunci yang masuk akal yang dapat memecahkan sandi tersebut.

Jika ciphertext yang tersedia lebih pendek dari Unicity Distance, ada kemungkinan beberapa kunci yang berbeda dapat menghasilkan plaintext yang terlihat masuk akal, membuat cryptanalysis menjadi ambigu. Namun, jika ciphertext melebihi Unicity Distance, pola redundansi bahasa mulai mendominasi, dan penyerang dapat menggunakan analisis statistik untuk mengeliminasi kunci-kunci yang salah dan menemukan kunci yang benar dengan probabilitas tinggi. Oleh karena itu, kriptosistem yang baik idealnya memiliki Unicity Distance yang sangat besar atau tak terhingga secara praktis.

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

# Langkah 1 — Perhitungan Entropi
def entropy(keyspace_size):
    """Menghitung Entropi Kunci (H(K)) dalam bit."""
    return math.log2(keyspace_size)

# Langkah 2 — Menghitung Unicity Distance
def unicity_distance(HK, R=0.75, A=26):
    """Menghitung Unicity Distance (U)."""
    # math.log2(A) = math.log2(26) ≈ 4.70
    return HK / (R * math.log2(A))

# Langkah 3 — Analisis Brute Force
def brute_force_time(keyspace_size, attempts_per_second=1e6):
    """Mengestimasi waktu brute force dalam hari."""
    seconds = keyspace_size / attempts_per_second
    days = seconds / (3600 * 24)
    return days

# Pengujian
keyspace_caesar = 26
keyspace_aes128 = 2**128

HK_caesar = entropy(keyspace_caesar)
HK_aes128 = entropy(keyspace_aes128)

print("--- Caesar Cipher (Keyspace = 26) ---")
print(f"Entropy H(K) = {HK_caesar:.2f} bit")
print(f"Unicity Distance U = {unicity_distance(HK_caesar):.2f} karakter")
print(f"Waktu Brute Force (1M/detik) = {brute_force_time(keyspace_caesar):.8f} hari")

print("\n--- AES-128 (Keyspace = 2^128) ---")
print(f"Entropy H(K) = {HK_aes128:.0f} bit")
print(f"Waktu Brute Force (1M/detik) = {brute_force_time(keyspace_aes128):.2f} hari")
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
1. Apa arti dari nilai entropy dalam konteks kekuatan kunci?Nilai entropi kunci ($H(K)$) mengukur tingkat ketidakpastian (randomness) dari kunci yang dipilih. Dalam konteks keamanan, entropi adalah ukuran langsung dari seberapa besar ruang kunci yang harus dicari oleh penyerang dalam serangan brute force. Entropi yang tinggi (misalnya, 128 bit) berarti ruang kunci ($2^{128}$) sangat besar, sehingga membutuhkan waktu eksponensial untuk dipecahkan, menjamin kekuatan kriptografi.

2. Mengapa unicity distance penting dalam menentukan keamanan suatu cipher?Unicity Distance ($U$) penting karena menentukan panjang minimum ciphertext yang diperlukan agar ciphertext tersebut menjadi rentan terhadap analisis statistik (seperti analisis frekuensi).Jika panjang ciphertext ($L$) lebih kecil dari $U$, ada beberapa kunci yang menghasilkan plaintext yang masuk akal, dan penyerang tidak dapat menentukan kunci yang benar (aman secara informasional).Jika $L$ melebihi $U$, redundansi bahasa (misalnya, $R=0.75$) mulai terungkap, memungkinkan penyerang untuk mengidentifikasi kunci yang benar dengan probabilitas tinggi. Cipher yang kuat harus memiliki $U$ yang sangat besar atau tak terbatas agar tidak rentan terhadap serangan ini.

3. Mengapa brute force masih menjadi ancaman meskipun algoritma sudah kuat?Brute force masih menjadi ancaman karena:Kunci yang Buruk/Lemah: Algoritma mungkin kuat (entropi tinggi), tetapi jika kunci yang dipilih pengguna mudah ditebak atau tidak benar-benar acak (entropi efektif rendah), brute force pada subset ruang kunci yang umum dapat berhasil dengan cepat.Kemajuan Teknologi: Peningkatan daya komputasi (GPU, komputasi terdistribusi, dan potensi komputer kuantum) terus meningkatkan kecepatan percobaan per detik, yang berarti ukuran kunci harus terus ditingkatkan untuk mengimbangi ancaman brute force di masa depan.
---

## 8. Kesimpulan
Praktikum ini berhasil mengimplementasikan perhitungan entropi kunci dan unicity distance, serta mensimulasikan waktu serangan brute force. Hasilnya menegaskan bahwa entropi tinggi (misalnya 128 bit pada AES) adalah prasyarat utama untuk keamanan kriptografi modern karena membuat brute force secara komputasi tidak mungkin. Sebaliknya, unicity distance yang pendek mengindikasikan bahwa ciphertext rentan terhadap serangan analisis frekuensi karena informasi bahasa dapat diekstrak dengan cepat.

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
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week4-entropy-unicity: implementasi Caesar Cipher dan laporan )
```
