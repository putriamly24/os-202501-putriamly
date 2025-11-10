
# Laporan Praktikum Minggu ke 5
Topik: Penjadwalan CPU - FCFS dan SJF

---

## Identitas
- **Nama**  : Putri Amaliya Rahmadani 
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Tujuan
1. Menghitung waiting time dan turnaround time untuk algoritma FCFS dan SJF.
2. Menyajikan hasil perhitungan dalam tabel yang rapi dan mudah dibaca.
3. Membandingkan performa FCFS dan SJF berdasarkan hasil analisis.
4. Menjelaskan kelebihan dan kekurangan masing-masing algoritma.
5. Menyimpulkan kapan algoritma FCFS atau SJF lebih sesuai digunakan.

---

## Dasar Teori
1. Pengertian Penjadwalan CPU
Penjadwalan CPU (CPU Scheduling) adalah proses yang mengatur urutan dari beberapa eksekusi proses  oleh prosesor agar penggunaan CPU ini menjadi lebih efisien.Tujuannya yaitu untuk lebih memaksimalkan kinerja pada sistem, mengurangi waktu tunggu proses, serta dapat meningkatkan throughput atau jumlah proses yang selesai dalam satu waktu.
2. Jenis-Jenis Algoritma Pemrogaman
   Terdapat beberapa jenis pada algoritma penjadwalan CPU, yaitu:
   - FCFS (First Come First Served)
   - SJF (Shortest Job First)
   - Priority Scheduling
   - Round Robin
   - Multilevel Queue Scheduling, dan lain sebagainya.
   Namun, pada praktikum ini hanya difokuskan pada dua algoritma utama yaitu FCFS dan SJF.
3. FCFS (First Come First Served)
Algoritma FCFS yang bertugas untuk menjalankan suatu proses sesuai dengan urutan kedatangan.Proses yang terlebih dahulu tiba akan dieksekusi terlebih dulu sampai selesai.Pada proses FCFS ini bersifat non-preemptive (proses yang tidak dapat dihentikan ditengah).Hal ini, mudah diterapkan serta adil, namun dapat mengakibatkan proses singkat jadi menunggu lebih lama kalau ada proses besar sebelumnya.
4. SJF (Shortest Job First)
 Algoritma SJF lebih mengutamakan proses serta waktu eksekusi yang paling singkat untuk dikerjakan lebih dulu.Proses ini dapat digunakan dengan bentuk non-preemptive atau preemptive.Algoritma ini lebih sesuai karena bisa mengurangi waktu tunggu yang rata-rata, tetapi terdapat kekurangan pada proses ini yaitu kesulitan dalam memperkirakan durasi proses yang dapat mengakibatkan starvation atau proses yang panjang.
5. Kesimpulan
Secara keseluruhan, algoritma FCFS lebih mudah untuk diterapkan, tetapi kurang efisien karena proses dengan durasi eksekusi panjang dapat menyebabkan proses lain menunggu lebih lama.Sementara itu, SJF mampu menghasil waktu tunggu rata-rata yang lebih singkat serta kinerja yang lebih baik, namun penerapannya akan lebih sulit karena memerlukan perkiraan waktu eksekusi yang lebih akurat.Oleh karena itu, pemilihan untuk algoritma penjadwalan perlu disesuaikan dengan baik yang sesuai pada kebutuhan serta karakterisik sistem yang digunakan. 

---

## Langkah Praktikum
1. **Siapkan Data Proses**
   Gunakan tabel proses berikut sebagai contoh (boleh dimodifikasi dengan data baru):
   | Proses |	Burst Time |	Arrival Time |
   |:--:|:--:|:--:|
   | P1 |	6 |	0 |
   | P2 |	8 |	1 |
   | P3 |	7 |	2 |
   | P4 |	3 |	3 |
   
2. **Eksperimen 1 – FCFS (First Come First Served)**
- Urutkan proses berdasarkan Arrival Time.
- Hitung nilai berikut untuk tiap proses:
```
Waiting Time (WT) = waktu mulai eksekusi - Arrival Time
Turnaround Time (TAT) = WT + Burst Time
```
- Hitung rata-rata Waiting Time dan Turnaround Time.
- Buat Gantt Chart sederhana:
```
| P1 | P2 | P3 | P4 |
0    6    14   21   24
```
  
3. **Eksperimen 2 – SJF (Shortest Job First)**
- Urutkan proses berdasarkan Burst Time terpendek (dengan memperhatikan waktu kedatangan).
- Lakukan perhitungan WT dan TAT seperti langkah sebelumnya.
- Bandingkan hasil FCFS dan SJF pada tabel berikut:

| Algoritma |	Avg Waiting Time |	Avg Turnaround Time |	Kelebihan |	Kekurangan |
|----------|-------------------|----------------------|-----------|------------|
| FCFS |	... |	... |	Sederhana dan mudah diterapkan |	Tidak efisien untuk proses panjang |
| SJF |	... |	... |	Optimal untuk job pendek |	Menyebabkan starvation pada job panjang |

4. **Eksperimen 3 – Visualisasi Spreadsheet (Opsional)**
- Gunakan Excel/Google Sheets untuk membuat perhitungan otomatis:
  - Kolom: Arrival, Burst, Start, Waiting, Turnaround, Finish.
  - Gunakan formula dasar penjumlahan/subtraksi.
- Screenshot hasil perhitungan dan simpan di:
```
praktikum/week5-scheduling-fcfs-sjf/screenshots/
```

5. **Analisis**
- Bandingkan hasil rata-rata WT dan TAT antara FCFS & SJF.
- Jelaskan kondisi kapan SJF lebih unggul dari FCFS dan sebaliknya.
- Tambahkan kesimpulan singkat di akhir laporan.
6. **Commit & Push**
```bash
git add .
git commit -m "Minggu 5 - CPU Scheduling FCFS & SJF"
git push origin main
```

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshots hasil](screenshots/FCFS-FJS.png)

---
## Hasil Eksekusi
- **Eksperimen 1 - FCFS (First Come First Served)**
  Tabel perhitungan:
  | Proses | Arrival | Burst | Start | Finish | Waiting Time = Start - Arrival | Turnaround Time = WT + Burst |
  |--------|---------|-------|-------|--------|--------------------------------|------------------------------|
  | P1 | 0 | 6 | 0 | 6 | 0 (0-0) | 6 (0+6) |
  | P2 | 1 | 8 | 6 | 14 | 5 (6-1) | 13 (5+8) |
  | P3 | 2 | 7 | 14 | 21 | 12 (14-2) | 19 (12+7) |
  | P4 | 3 | 3 | 21 | 24 | 18 (21-3) | 21 (18+3) |

 Penjumlahan rata-rata:
 - Total WT = 0 + 5 + 12 + 18 = 35
   Rata-rata pada WT = 35/4 = 8.75
 - Total TAT = 6 + 13 + 19 + 21 = 59
   Rata-rata pada TAT = 59/4 = 14.75

- **Eksperimen 2 - SJF (Shortest Job First)**
  Urutan pada atau yang berdasarkan kondisi arrival dan burst saat pemilihan:
  - Pada t = 0:hanya P1 (burst 6) yang tersedia - jalankan P1.
  - P1 selesai pada t = 6. Proses yang sudah sampai di t = 6:P2 (8), P3 (7), P4 (3).Pilihlah burst yang paling pendek yaitu P4.
  - Setelah P4 selesai (t=9), tersisa P2 (8) dan P3 (7) yaitu pilih yang P3 (7) lalu P2 (8).
  Tabel perhitungan:

| Proses | Arrival | Burst | Start | Finish | Waiting Time = Start - Arrival | Turnaround Time = WT + Burst |
|--------|---------|-------|-------|--------|--------------------------------|------------------------------|
| P1 | 0 | 6 | 0 | 6 | 0 (0-0) | 6 (0+6) |
| P4 | 3 | 3 | 6 | 9 | 3 (6-3) | 6 (3+3) |
| P3 | 2 | 7 | 9 | 16 | 7 (9-2) | 14 (7+7) |
| P2 | 1 | 8 | 16 | 24 | 15 (16-1) | 23 (15+8) |

 Penjumlahan dan rata-rata:
 - Total WT = 0 + 3 + 7 + 15 = 25
   Rata-rata WT = 25 /4 = 6.25
- Total TAT = 6 + 6 + 14 + 23 = 49
   Rata-rata TAT = 49 / 4 = 12.25

- **Perbandingan**
  
  | Algoritma | Rata-rata WT | Rata-rata TAT |
  |-----------|--------------|---------------|
  | FCFS | 8.75 | 14.75 |
  | SJF | 6.25 | 12.25 | 
   
- **Kesimpulan**
  - SJF lebih efisien karena dapat menghasilkan waktu tunggu dan penyelesaian rata-rata yang lebih kecil.
  - FCFS lebih sederhana serta adil, tapi masih kurang dalam mengoptimalkan proses yang memiliki waktu eksekusi berbeda-beda.
  
## Analisis
-  Perbandingan hasil (angka):
   - FCFS (First Come First Served)
    - Average Waiting Time (WT) = 8.75
    - Average Turnaround Time (TAT) = 14.75
   - SJF (Shortest Job First)
    - Average Waiting Time (WT) = 6.25
    - Average Turnaround Time (TAT) = 12.25
  - Perbedaan antara FCFS dan SJF 
    - Pengurangan pada rata-rata WT = 2.5 unit-28.75% yang lebih kecil dibandingkan dengan FCFS.
    - Pengurangan pada rata-rata TAT = 2.5 unit-16.95% yang lebih kecil dibandingkan dengan FCFS.
-  SJF lebih unggul daripada FCFS
   SJF akan lebih unggul dari FCFS jika beberapa kondisi dapat terpenuhi:
   - Waktu eksekusi (burst time) proses yang dapat diketahui dengan cukup akurat atau proses yang bisa diperkirakan.
   - Beban kerja yang terdiri dari banyak proses dengan durasi waktu yang berbeda ataupun banyak sekali proses yang pendek berdatangan.
   - Lingkungan batch / non-interaktif menjadi tujuan utama dalam meminimalkan WT/TAT.
   - Overhead yang digunakan untuk memilih proses terpendek yang bisa ditanggung scheduling cost rendah dibanding dari keuntungan.
   Pada situasi seperti itu SJF dapat memaksimalkan proses penyelesaian menjadi lebih singkat atau cepat sehingga dapat menurunkan rata-rata waiting atau turnaround.
-  FCFS lebih unggul daripada SJF
   FCFS lebih unggul dari SJF jika dapat melibatkan:
   - Keadilan prekditabilitas sangan penting atau urutan kedatangan yang dipertahankan.
   - Waktu burst tidak diketahui atau sulit jika diperkirakan.
   - Sistem interaktif dapat ringan yang membutuhkan respon adil untuk tiap pengguna.
   - Implementasi harus secara sederhana tanpa overhead atau penjadwalan yang kompleks.
- Kesimpulan
  Pada eksperimen yang dijalankan, SJF mengalahkan FCFS atau rata-rata WT turun dari 8.75 menjadi 6.25 dan TAT dari 14.75 menjadi 12.25.
  Pada dasarnya dapat dianalisis dengan pilih SJF untuk lingkungan batch dengan informasi burst yang sudah tersedia untuk tujuan utamanya yaitu menurunkan rata-rata waktu tunggu, serta pilih FCFS untuk kesederhanaan pada sistem interaktif yang tidak bisa diperkirakan.
  

---

## Kesimpulan
1. SJF dapat menunjukan hasil yang lebih efisien, karena dapat menekan rata-rata pada waktu tunggu serta waktu penyelesaian dibandingkan dengan FCFS.
2. FCFS mempunyai cara kerja yang sederhana serta adil, tatapi dapat membuat proses yang singkat dan menunggu lama jika ada proses besar yang datang lebih awal.
3. Pada pemilihan algoritma harus disesuaikan bersama kebutuhan sistem - SJF lebih cocok kepada sistem yang fokus pada kecepatan penyelesaian, sedangkan FCFS lebih sesuai pada sistem yang mengutamakan urutan serta keadilan eksekusi.

---

## Quiz
1. Apa perbedaan utama antara FCFS dan SJF?
   Jawaban:
   | Aspek | FCFS (First Come First Served) | SJF (Shortest Job First) |
   |-------|--------------------------------|--------------------------|
   | Jenis algoritma | Kadang non-preemptive (tidak dapat dipotong di tengah). | Dapat non-preemptive ataupun preemptive (SRTF). |
   | Cara Kerja | Proses yang dikerjakan harus sesuai pada urutan kedatangan. | Proses yang dikerjakan dengan waktu eksekusi paling singkat alangkah baiknya dijalankan terlebih dahulu. |
   | Watktu tunggu rata-rata | Proses lebih panjang atau lama dan bisa membuat proses yang lain menunggu. | Proses lebih cepat karena prosesnya singkat dan segera diselesaikan. |
   | Keadilan | Prosesnya adil karena berdasarkan siapa yang datang duluan. | Prosesnya kurang adil karena proses yang lama dapat tertunda. |  
2. Alasan SJF menghasilkan waktu tunggu rata-rata paling kecil?
   Jawaban: Alasannya karena SJF lebih memprioritaskan proses dengan waktu kerja paling cepat terlebih dahulu.Dengan adanya hal tersebut, dapat mengakibatkan proses yang kecil cepat selesai dan waktu tunggu keseluruhan menjadi lebih singkat.SJF juga dapat dikatakan sebagai algoritma paling efisien untuk mengurangi rata-rata pada waktu tunggu.
3. Kekurangan SJF di sistem interaktif? 
   Jawaban:
   Proses yang menggunakan SJF memiliki beberapa kendalan yang meliputi:
- Kesulitan dalam menebak waktu pada proses yang  dijalankan, karena durasi yang tidak pasti.
- Proses yang besar dapat tertunda jika selalu ada proses kecil yang berdatangan terus.
- Kurang cepat dalam menanggapi pengguna, yang mengakibatkan ketidak cocokan untuk sistem yang membutuhkan respon langsung.

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
