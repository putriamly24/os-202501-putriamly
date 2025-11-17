
# Laporan Praktikum Minggu  6
Topik: Penjadwalan CPU – Round Robin (RR) dan Priority Scheduling

---

## Identitas
- **Nama**  : Putri Amaliya Rahmadani 
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Deskripsi Singkat
Pada praktikum minggu ini, mahasiswa akan mempelajari **dua algoritma lanjutan penjadwalan CPU**, yaitu:
- **Round Robin (RR)**  
- **Priority Scheduling**

Kedua algoritma ini banyak digunakan pada sistem modern karena mempertimbangkan **keadilan waktu eksekusi (time quantum)** dan **tingkat prioritas proses**.  
Mahasiswa akan melakukan simulasi perhitungan manual untuk menghitung *waiting time* dan *turnaround time*, serta menganalisis efek perbedaan *time quantum* dan prioritas terhadap performa CPU scheduling.

---


## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:
1. Menghitung waiting time dan turnaround time pada algoritma RR dan Priority.
2. Menyusun tabel hasil perhitungan dengan benar dan sistematis.
3. Membandingkan performa algoritma RR dan Priority.
4. Menjelaskan pengaruh time quantum dan prioritas terhadap keadilan eksekusi proses.
5. Menarik kesimpulan mengenai efisiensi dan keadilan kedua algoritma.


---

## Dasar Teori
1. Round Robin (RR) adalah metode penjadwalan CPU yang setiap prosesnya dijalankan secara bergiliran atau sesuai dengan waktu yang telah ditentukan, sehingga pada setiap proses akan mendapatkan urutan yang adil.
2. Time Quantum adalah waktru maksimum yang diberikan CPU untuk menjalankan satu proses didalam metode Round Robin.Jika proses terlalu kecil, maka sistem akan responsif tetapi banyak proses yang pindah, jika proses terlalu besar, maka proses yang lain akan menunggu lebih lama lagi tetapi CPU akan lebih efisien.
3. Turnaround Time adalah waktu total yang dibutuhkan proses pada saat masuk ke sistem sampai selesai atau finish.Turnaround time dapat dihitung melalui mengurangi waktu kedatangan dari waktu selesai proses.
4. Waiting Time adalah total waktu yang dihabiskan proses untuk menunggu giliran CPU, pada proses waiting time waktu menunggu diperoleh dari selisih antara turnaround time dengan burst time.
5. Priority Scheduling adalah metode penjadwalan CPU yang prosesnya dijalankan melalui prioritas, sehingga dapat menyebabkan proses yang prioritas tinggi dijalankan terlebih dahulu.Namun, proses dengan prioritas rendah dapat mengalami starvation, dan metode ini dapat bersifat preemptive ataupun non-preemptive.

---
## Langkah Praktikum
1. Langkah-langkah yang dilakukan.
2. Perintah yang dijalankan.
3. File dan kode yang dibuat.
4. Commit message yang digunakan.

---


## Kode / Perintah
1. **Siapkan Data Proses** Gunakan contoh data berikut (boleh dimodifikasi sesuai kebutuhan):

| Proses |	Burst Time |	Arrival Time |	Priority |
|:--:|:--:|:--:|:--:|
| P1 |	5 |	0 |	2 |
| P2 |	3 |	1 |	1 |
| P3 |	8 |	2 |	4 |
| P4 |	6 |	3 |	3 |
2. **Eksperimen 1 – Round Robin (RR)**

- Gunakan time quantum (q) = 3.
- Hitung waiting time dan turnaround time untuk tiap proses.
- Simulasikan eksekusi menggunakan Gantt Chart (manual atau spreadsheet).

```
| P1 | P2 | P3 | P4 | P1 | P3 | ...
0    3    6    9   12   15   18  ...
```

- Catat sisa burst time tiap putaran.
3. **Eksperimen 2 – Priority Scheduling (Non-Preemptive)**

- Urutkan proses berdasarkan nilai prioritas (angka kecil = prioritas tinggi).
- Lakukan perhitungan manual untuk:
```
WT[i] = waktu mulai eksekusi - Arrival[i]
TAT[i] = WT[i] + Burst[i]
```
- Buat tabel perbandingan hasil RR dan Priority.
4. **Eksperimen 3 – Analisis Variasi Time Quantum (Opsional)**

- Ubah quantum menjadi 2 dan 5.
- Amati perubahan nilai rata-rata waiting time dan turnaround time.
- Buat tabel perbandingan efek quantum.
5. **Eksperimen 4 – Dokumentasi**

- Simpan semua hasil tabel dan screenshot ke:

``praktikum/week6-scheduling-rr-priority/screenshots/``

- Buat tabel perbandingan seperti berikut:

| Algoritma |	Avg Waiting Time |	Avg Turnaround Time	| Kelebihan |	Kekurangan |
|-----------|------------------|----------------------|-----------|------------|
| RR |	... |	... | Adil terhadap semua proses |	Tidak efisien jika quantum tidak tepat |
| Priority |	... |	... |	Efisien untuk proses penting |	Potensi starvation pada prioritas rendah |


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
- Round Robin akan menjamin pada setiap proses mendapatkan giliran CPU secara adil dan urut, sedangkan Priority Scheduling akan lebih menekankan eksekusi proses berdasarkan prioritas.
- Time Quantum memengaruhi performa pada sistem, jika quantum kecil yang membuat sistem responsif tetapi banyak context switching, sedangkan pada quantum besar akan lebih efisien yang membuat respons lain jadi lambat.
- Turnaround Time dan Waiting Time  menjadi indikator penting yang digunakan untuk menilai efisiensi dan fairness penjadwalan CPU.
  
---

## Tugas
1. Hitung waiting time dan turnaround time untuk algoritma RR dan Priority.  
3. Sajikan hasil perhitungan dan Gantt Chart dalam laporan.md.
4. Bandingkan performa dan jelaskan pengaruh time quantum serta prioritas.

## Quiz
1. Apa perbedaan utama antara Round Robin dan Priority Scheduling?
   Perbedaan yang utama dari segi penjadwalan (scheduling) antara lain:
   - Round Robin: penjadwalan (scheduling) yang berdasarkan urutan dengan time quantum, tanpa melihat penting atau tidaknya proses.
   - Priority Scheduling: penjadwalan yang berdasarkan prioritas, atau proses dengan prioritas tertinggi yang didahulukan dari proses lain.
2. Apa pengaruh besar/kecilnya time quantum terhadap performa sistem?
 - Time *Quantum Kecil*
   - Kelebihan :
     - Pada sistem akan terasa lebih cepat saat merespon karena proses sering mendapatkan urutan atau giliran.
     - Proses bagus untuk progam yang masih memerlukan reaksi segera.
   - Kekurangan :
     - Pergantian pada proses sangan sering yang menyebabkan waktu CPU banyak yang terbuang.
     - Kinerja pada sistem sering menurun karena terlalu banyak overhead.
 - Time *Quantum Besar*
   - Kelebihan :
     - Context switching lebih sedikit yang menyebabkan proses CPU lebih optimal.
     - Proses yang panjang dapat berjalan lebih lancar dan cepat.
   - Kekurangan :
      - Kurangnya responsif pada sistem yang dijalankan.
      - Dapat menunggu proses yang lain menunggu lebih lama.
 - Kesimpulan:
      - Time quantum harus dipilih secara seimbang, kalau terlalu dapat membuat sistem menjadi responsif tetapi lebih boros pada performa, sementara jika terlalu besar dapat membuat sistem efisien tetapi lebih lambat dalam merespon.Quantum lebih ideal memberikan keseimbangan pada respons cepat dan efisien CPU.
        
3. Mengapa algoritma Priority dapat menyebabkan starvation?
  - Algoritma Priority dapat menyebabkan starvation karena proses yang prioritasnya rendah akan terus menunggu jika selalu ada proses yang prioritas tinggi berdatangan.Alhasil, proses rendah bisak tidak pernah dijalankan ataupun prosesnya terlupakan sehingga tidak pernah selesai, inilah yang sering disebut starvation. 

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
