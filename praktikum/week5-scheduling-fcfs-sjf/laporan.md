
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
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

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

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

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
