
# Laporan Praktikum Minggu Ke 4
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Putri Amaliya Rahmadani 
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:
1. Menjelaskan konsep proses dan user dalam sistem operasi Linux.
2. Menampilkan daftar proses yang sedang berjalan dan statusnya.
3. Menggunakan perintah untuk membuat dan mengelola user.
4. Menghentikan atau mengontrol proses tertentu menggunakan PID.
5. Menjelaskan kaitan antara manajemen user dan keamanan sistem.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

---

## Langkah Praktikum
1. **Setup Environment**
  - Gunakan Linux (Ubuntu/WSL).
  - Pastikan Anda sudah login sebagai user non-root.
  - Siapkan folder kerja:
``praktikum/week4-proses-user/``
2. **Eksperimen 1 – Identitas User**
 Jalankan perintah berikut:
```bash
whoami
id
groups
```
- Jelaskan setiap output dan fungsinya.
- Buat user baru (jika memiliki izin sudo):
  ```bash
  sudo adduser praktikan
  sudo passwd praktikan
  ```
- Uji login ke user baru.
3. **Eksperimen 2 – Monitoring Proses**
  Jalankan:
```bash
ps aux | head -10
top -n 1
```
- Jelaskan kolom penting seperti PID, USER, %CPU, %MEM, COMMAND.
- Simpan tangkapan layar `top` ke:
  ```
  praktikum/week4-proses-user/screenshots/top.png
  ```
4. **Eksperimen 3 – Kontrol Proses**
- Jalankan program latar belakang:
  ```bash
  sleep 1000 &
  ps aux | grep sleep
  ```
- Catat PID proses sleep.
- Hentikan proses:
  ```bash
  kill <PID>
  ```
- Pastikan proses telah berhenti dengan ps aux | grep sleep.
5. **Eksperimen 4 – Analisis Hierarki Proses**
  Jalankan:
  ```bash
  pstree -p | head -20
  ```
  - Amati hierarki proses dan identifikasi proses induk (init/systemd).
  - Catat hasilnya dalam laporan.
6. **Commit & Push**
```bash
git add .
git commit -m "Minggu 4 - Manajemen Proses & User"
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
![Screenshot hasil](<screenshots/eksperimenputri1>)
![Screenshot hasil](<screenshots/eksperimenputri2>)
![Screenshot hasil](<screenshots/eksperimenputri3>)

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
1. Apa fungsi dari proses `init` atau `systemd` dalam sistem Linux?  
   Jawaban: Proses `init` atau `systemd` adalah proses yang pertama dikerjakan oleh kernel pada saat komputer dengan sistem Linux dinyalakan.Peran utamanya yaitu mengatur dan mengerjakan seluruh sistem agar dapat berfungsi dengan baik dan normal.  
2. Apa perbedaan antara `kill` dan `killall`?
   Jawaban:    

    | Perintah | Fungsi | Contoh | Keterangan |
   |----------|--------|--------|------------|
   | `kill` | Mengirim sinyal yang digunakan untuk menghentikan pada satu proses tertentu berdasarkan PID (Process ID) | `kill 12234` | Menghentikan proses dengan ID 1234 saja |
   | `killall` | Mengirimkan sinyal yang digunakan untuk menghentikan pada semua proses dengan nama progam yan sama | `killall firefox` | Menghentikan semua proses yang bernama "firefox" |

    Jadi `kill` digunakan kalau mengetahui nomor prosesnya (PID),sedangkan `killall` digunakan kalau mengetahui nama dari progamnya.
4. Mengapa user `root` memiliki hak istimewa di sistem Linux?  
   Jawaban: Karena user `root`mempunyai hak istimewa yang diperlukan:
   -  Untuk mengatur seluruh sistem,termasukjuga menginstal sebuah aplikasi,menghapus,dan memperbaiki progam.
   -  Mempunyai hak akses penuh ke dalam semua file dan direktori, tanpa batasan izin.
   -  Membutuhkan satu pengguna yang dapat mengontrol seluruh aspek pada sistem,termasuk keamanan dan konfigurasi.
     Jadi kesimpulannya karena user `root` mempunyai hakistimewa karena berperan sebagai administrator utama yang mempunyai tanggung jawab atas pengolahan dan pengamanan pada seluruh sistem di Linux.  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
