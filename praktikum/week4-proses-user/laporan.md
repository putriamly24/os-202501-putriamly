
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

## Tugas & Quiz
## Tugas
1. Dokumentasi hasil perintah dan fungsi
   | No | Perintah yang Dieksekusi | Output yang Terlihat | Fungsi Perintah |
   |----|--------------------------|----------------------|------------------|
   | 1 | `sudo adduser praktikan` | Menambahkan pengguna praktikan dengan UID/GID 1000 dan group utama di `praktikan`.Meminta lebih detail info pengguna dan kata sandi baru. | Digunakan untuk menambah akun pengguna baru ke dalam sistem Linux, termasuk memubuat direktori `home` dan `shell` secara defalut. |
   | 2 | `grup praktikan {root}` | Tidak tereksekusi,masih ada terjadi kesalahan ketik pada gambar. | Maksudnya yaitu groups `root`: Menampilkan daftar grup yang menunjukan pengguna `root` menjadi anggotanya. |
   | 3 | `sudo adduser praktikan users` | Menambahkan pengguna `praktikan` ke grup yang ada tambahan users. | Digunakan untuk menambahkan pengguna yang sudah atau lebih grup tambahan. |
   | 4 | ` ps aux` | `head -10` | Menampilkan daftar 10 dari proses teratas (termasuk header) yang sedang bekerja di sistem, dengan detail seperti PID,%CPU,%MEM%, dan COMMAND. |
   | 5 | `top` | Menampilkan monitor pada saat proses interaktif waktu nyata (real-time) yang diperbarui secara bertahap, yang menunjukan pengguna CPU, Memori (RAM), dan daftar proses yang sedang bekerja di sistem.| Memantau kinerja pada sistem dan proses secara dinamis dan detail. |
   | 6 | `sleep 1000 &` | Pada proses `sleep` dieksekusi di background dengan PID 729, dan akan menunggu selama kurang lebih 1000 detik. | Menangguhkan eksekusi selama waktu yang sudah ditentukan.Tanda dan proses menjalaknkannya di background. |
   | 7 | `ps aux` | `grep sleep` | Menemukan proses `sleep` yang sedang bekerja (PID 729) dan proses `grep` itu sendiri.|
   | 8 | `kill <PID>` | Proses yang gagal karena `kill <PID>` pada gambar tidak tereksekusi dengan PID. | Mengirimkan sinyal secara default TERM ke proses dengan PID tertentu untuk mengkhirinya secara normal. |
   | 9 | `pstree -p` | `head -20` | Menampilkan hierarki prosses(PID yang disertakan) ke dalam format diagram pohon, dibatasi 20 baris. |

 2.  Diagram pohon hierarki proses (`pstree`).
 3.  Hubungan user management dan keamanan sistem Linux.
     Manajemen pengguna adalah fondasi yang utama pada keamanan di Linux.
     1. Prinsip hak akses paling kecil:
        - Setiap pengguna (UID) dan grup (GID) hanya akan diberi izin yang benar-benar dibutuhkan (baca/tulis/eksekusi).
        - Prinsip ini membatasi potensi terjadinya kerusakan, karena pengguna biasa (non-root) tidak akan bisa mengubah atau merusak file pada sistem yang krusial.
      2. Pemisahan kewenangan (kontrol root)
         - Memisahkan akun Superuser (`root`) yang tidak terbatas dengan pengguna biasa yang akan dibatasi.
         - Pengguna `sudo` memastikan pengguna biasa hanya meminjam izin `root` sementara untuk tugas yang spesifik, sehingga sistem tidak akan rentan karena kesalahan-kesalahan ceroboh yang dilakukan oleh pengguna biasa.
      3. Akuntabilitas
         - Setiap tindakan pada proses akan dicatat yang berdasarkan akun pengguna yang login.
         - Proses ini akan memudahkan identifikasi siapa yang bertanggung jawab atau penyebab error pada saat terjadi masalah keamanan atau anomali di sistem.
      Kesimpulan yaitu untuk mengontrol pengguna adalah cara paling efektif untuk mengontrol pada saat terjanya resiko.Dengan batasan yang jelas,sistem Linux bisa mencegah penyalahgunaan dan membatasi dampak serangan atau kesalahan pada sistem Linux yang berjalan.    
   
   
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
