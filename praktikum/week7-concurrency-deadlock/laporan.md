
# Laporan Praktikum Minggu 7
Topik: Sinkronisasi Proses dan Masalah Deadlock
 
---

## Identitas Kelompok
  *Nama*  :
  1. Rafika Rahma (250202917)
  2. Putri Amaliya Rahmadani (250202924)
  3. Keysya Ayu Anggita (250202944)
     
  *Kelas* : 1 IKRA
---
## Pendahuluan
Dalam sistem operasi, banyak proses sering berjalan pada waktu yang hampir bersamaan. Agar semua proses dapat berfungsi dengan baik dan tidak saling mengganggu, diperlukan mekanisme sinkronisasi yang mengatur bagaimana proses berbagi dan menggunakan sumber daya. Tanpa pengaturan yang tepat, sistem dapat mengalami deadlock, yaitu keadaan ketika beberapa proses berhenti total karena saling menunggu sumber daya yang tidak pernah tersedia. Situasi seperti ini merugikan karena membuat sistem tidak dapat bekerja secara optimal.

Untuk memahami permasalahan tersebut, praktikum ini menggunakan Dining Philosophers Problem sebagai contoh. Masalah ini menjelaskan lima proses (filosof) yang harus berbagi sumber daya terbatas (fork), menjadikannya alat yang ideal untuk menganalisis deadlock dan menerapkan mekanisme pencegahan.

Pada praktikum, mahasiswa menguji dua versi implementasi: versi pertama yang membiarkan proses berjalan tanpa pencegahan deadlock, dan versi kedua yang menggunakan mekanisme sinkronisasi seperti semaphore atau monitor. Melalui perbandingan kedua versi ini, mahasiswa dapat melihat secara langsung bagaimana deadlock terjadi serta bagaimana solusi sinkronisasi dapat mencegahnya.

Selain memperdalam konsep teknis, praktikum ini juga membantu mahasiswa bekerja sama dalam tim dan menyusun analisis secara lebih runtut dan sistematis.
## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:
1. Mengidentifikasi empat kondisi penyebab deadlock (mutual exclusion, hold and wait, no preemption, circular wait).
2. Menjelaskan mekanisme sinkronisasi menggunakan semaphore atau monitor.
3. Menganalisis dan memberikan solusi untuk kasus deadlock.
4. Berkolaborasi dalam tim untuk menyusun laporan analisis.
5. Menyajikan hasil studi kasus secara sistematis.
---

## Dasar Teori
Deadlock adalah keadaan dalam sistem operasi di mana dua atau lebih proses tidak dapat melanjutkan eksekusinya karena masing-masing saling menunggu sumber daya yang sedang digunakan oleh proses lain. Kondisi ini menyebabkan proses-proses tersebut terhenti secara permanen, sehingga tidak ada satupun yang dapat bergerak maju. Deadlock sering muncul pada lingkungan multitasking yang melibatkan alokasi sumber daya secara bersamaan, seperti perangkat keras, file, lock, atau variabel sinkronisasi.

Dalam sistem komputer, deadlock biasanya terjadi ketika proses membutuhkan lebih dari satu sumber daya untuk menyelesaikan pekerjaannya. Ketika sumber daya terbatas atau bersifat eksklusif, proses dapat terjebak dalam situasi saling menunggu yang tidak dapat diselesaikan tanpa intervensi dari sistem operasi. Untuk menganalisis kondisi ini, sistem umumnya menggunakan model hubungan antara proses dan sumber daya, misalnya melalui resource-allocation graph, untuk melihat pola menunggu yang berpotensi membentuk siklus.

Deadlock hanya terjadi apabila empat kondisi berikut muncul secara bersamaan.
- Mutual Exclusion - sumber daya hanya dapat digunakan oleh satu proses pada satu waktu.
- Hold and Wait - proses memegang satu sumber daya sambil menunggu sumber daya lain yang masih digunakan proses lain.
- No Preemption - tidak dapat diambil paksa oleh sistem dan hanya dilepas secara sukarela.
- Circular Wait - rantai proses yang saling menunggu sumber daya satu sama lain dalam pola melingkar.

---

## Langkah Pengerjaan
1. **Persiapan Tim**
   - Bentuk kelompok beranggotakan 3–4 orang.  
   - Tentukan ketua dan pembagian tugas (analisis, implementasi, dokumentasi).

2. **Eksperimen 1 – Simulasi Dining Philosophers (Deadlock Version)**
   - Implementasikan versi sederhana dari masalah *Dining Philosophers* tanpa mekanisme pencegahan deadlock.  
   - Contoh pseudocode:
     ```text
     while true:
       think()
       pick_left_fork()
       pick_right_fork()
       eat()
       put_left_fork()
       put_right_fork()
     ```
   - Jalankan simulasi atau analisis alur (boleh menggunakan pseudocode atau diagram alur).  
   - Identifikasi kapan dan mengapa deadlock terjadi.

3. **Eksperimen 2 – Versi Fixed (Menggunakan Semaphore / Monitor)**
   - Modifikasi pseudocode agar deadlock tidak terjadi, misalnya:
     - Menggunakan *semaphore (mutex)* untuk mengontrol akses.
     - Membatasi jumlah filosof yang dapat makan bersamaan (max 4).  
     - Mengatur urutan pengambilan garpu (misal, filosof terakhir mengambil secara terbalik).  
   - Analisis hasil modifikasi dan buktikan bahwa deadlock telah dihindari.

4. **Eksperimen 3 – Analisis Deadlock**
   - Jelaskan empat kondisi deadlock dari versi pertama dan bagaimana kondisi tersebut dipecahkan pada versi fixed.  
   - Sajikan hasil analisis dalam tabel seperti contoh berikut:

     | Kondisi Deadlock | Terjadi di Versi Deadlock | Solusi di Versi Fixed |
     |------------------|---------------------------|------------------------|
     | Mutual Exclusion | Ya (satu garpu hanya satu proses) | Gunakan semaphore untuk kontrol akses |
     | Hold and Wait | Ya | Hindari proses menahan lebih dari satu sumber daya |
     | No Preemption | Ya | Tidak ada mekanisme pelepasan paksa |
     | Circular Wait | Ya | Ubah urutan pengambilan sumber daya |

5. **Eksperimen 4 – Dokumentasi**
   - Simpan semua diagram, screenshot simulasi, dan hasil diskusi di:
     ```
     praktikum/week7-concurrency-deadlock/screenshots/
     ```
   - Tuliskan laporan kelompok di `laporan.md` (format IMRaD singkat: *Pendahuluan, Metode, Hasil, Analisis, Diskusi*).

6. **Commit & Push**
   ```bash
   git add .
   git commit -m "Minggu 7 - Sinkronisasi Proses & Deadlock"
   git push origin main
---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```
while true:
  think()
  pick_left_fork()
  pick_right_fork()
  eat()
  put_left_fork()
  put_right_fork()
```


---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

## Tugas & Quiz
## Tugas
1. Analisis versi Dining Philosophers yang menyebabkan deadlock dan versi fixed yang bebas deadlock.
2. Dokumentasikan hasil diskusi kelompok ke dalam laporan.md.
3. Sertakan diagram atau screenshot hasil simulasi/pseudocode.
4. Laporkan temuan penyebab deadlock dan solusi pencegahannya.
## Quiz
**1. Sebutkan empat kondisi utama penyebab deadlock.**
   
   *Jawaban:*

   - Mutual Exclusion: Sumber daya hanya bisa dipakai satu proses.
   - Hold and Wait: Proses memegang satu sumber daya sambil menunggu yang lain.
   - No Preemption: Sumber daya tidak bisa direbut paksa.
   - Circular Wait: Proses saling menunggu membentuk lingkaran.
     
**2. Mengapa sinkronisasi diperlukan dalam sistem operasi?**
   
    *Jawaban:*

   Sinkronisasi diperlukan dalam sistem operasi karena proses atau thread yang berjalan secara bersamaan dapat saling mengganggu ketika mengakses sumber daya atau data yang sama. Tanpa mekanisme sinkronisasi, dapat terjadi race condition yang membuat hasil eksekusi tidak dapat diprediksi, serta menimbulkan ketidakkonsistenan data, misalnya ketika beberapa proses melakukan pembaruan pada variabel yang sama secara bersamaan. Sinkronisasi juga memastikan penggunaan sumber daya bersama dilakukan secara aman dan bergiliran, sehingga konflik dapat dihindari. Selain itu, sinkronisasi membantu menjaga ketepatan eksekusi paralel pada sistem multicore dan mencegah masalah seperti deadlock atau livelock dengan mengatur urutan dan akses proses terhadap sumber daya. Secara keseluruhan, sinkronisasi menjadi kunci agar sistem dapat berjalan stabil, benar, dan konsisten meskipun banyak proses berjalan secara simultan.

**3. Jelaskan perbedaan antara semaphore dan monitor.**
   
    *Jawaban:*

   | Semaphore | Monitor |
   | :--- | :--- |
   | Mekanisme sinkronasisasi tingkat rendah (low-level) | Mekanisme sinkronisasi tingkat tinggi (high_level) |
   | Menggunakan counter dan operasi wait() dan sigmal() | Menggunakan condition variable dan prosedur terin tegrasi |
   | Programmer harus mengelola sendiri kapan kunci diambil/dilepas (rawan error) | Pengelolaan kunci dilakukan otomatis oleh monitor (lebih aman) |
   | Dapat menyebabkan deadlock jika salah penggunaan | Mengurangi resiko deadlock karena struktur lebih terkontrol |

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
