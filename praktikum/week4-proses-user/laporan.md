
# Laporan Praktikum Minggu Ke 4
Topik: Pemahaman Pross dan Kinerja Sistem Operasi Linux

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
1. Kernel merupakan inti dari sitem operasi yang memilik tugas untuk mengatur seluruh sumberdaya pada komputer, termasuk proses,memori]], dan juga perangkat keras.
2. Proses ini merupakan salah satu progam yang dikerjakan pada sistem; setiap proses mempunyai PID (Process ID) dan bisa memiliki hubungan induk-anak (parent-child).
3. System call merupakan mekanisme yang dapat digunakan pada progam di user space untuk meminta layanan dari kernel, seperti membuat proses (`fork()`),mengerjakan progam (`exec()`), ataupun dapat menghentikan proses(`kill()`).
4. Manajemen proses dapat mencakup pembuatan, penjadwalan, pemantauan, dan menghentikan proses, yang semua sistemnya diatur oleh kernel agar sistem berjalan secara efisen.
5. Lingkungan Linux sudah menyediakan berbagai perintah seperti `ps,top,pstree`, dan `kill` untuk melihat dan mengontrol semua proses yang bekerja di sistm.

---

## Langkah Praktikum`
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
## Hasil Ekperimen 
- **Ekperimen 1 - Identitas User**
  Bertujuan untuk melihat dan mengetahui identitas user yang sedang aktif dan dapat membuat user baru.
  Perintah-perintah yang dijalankan:
  - `whoami`
  - `id`
  - `groups`
  - `sudo adduser praktikan`
  - `sudo passwd praktikan`
  Untuk Output dari `whoami` dapat menunjukan kalau `root` - berarti terminal yang sedang bekerja sebagai user `root`.Pada saat `sudo 
  adduser praktikan` sistem akan menampilkan:
    Adding new user `praktikan`(1000)- user yang baru dibikin menggunakan UID/GID 1000.Home directory dibuat `/home/praktikan`.Setelah itu diminta untuk memasukan pssword dan iformasi pada profil (Full Name, Room Number, dsb) - pada foto diisi,seperti (`putriamly,room2410` phone `1234567`).
    Pada Proses pembuatan `sudo passwd praktian` berhasil saat mengubah password ( `passwd: password updated successfullly`).
    Analiis singkatnya yaitu pada saat proses pembuatan user berhasil; Linux akan menambahkan entry user (UID 1000) serta folder home, dan akan menambahkan ke grup users.`whoami/id/groups` sangatt berguna untuk memastikan identitas serta hak akses pada saat menjalankkan eksperimen.
    Kesimpulan eksperimen 1:
    User baru praktikan telah berhasil dibikin serta bisa di-login (account yang siap pakai).Sistem dapat mengenali user `root` sebagai pengguna yang menjalankan percobaan.

    ---
- **Eksperimen 2 - Monitoring Proses**
  Tujuannya yaitu untuk memantau pada saat proses yang bekerja dan membaca kolom penting (PID, USER, %CPU, %MEM, COMMAND).
  Perintah yang dikerjakan:
  ```bash
  ps aux | head -10
  top -n 1
  ```
  Menghasilkan:
  `ps aux`menampilkan beberapa dafrat proses disertai kolom: USER, PID, %CPU, %MEM, VSZ,RSS, STAT, START, TIME,COMMAND.
  Proses ini membuktikan sistem dapat memantau seluruh aktiitas pada proses yang sedang bekerja di latar depan maupun belakang.

  ---
- **Eksperimen 3 - Kontrol Proses**
  Pada percobaan ini perintah progam yang menjadi latar belakan:
  ```bash
  sleep 1000 &
  ps aux | grep sleep
  ```
  Perinta `sleep 1000 &` mengerjakan proses `sleep` pada background, serta `ps aux`| grep sleep` yang digunakan untuk menampilkan PID-nya.Untuk proses yang berkelanjutan akan dibutuhkan:
  ```bash
  kill <PID>
  ```
  dan akan diverifikasi kembali menggunakan:
  ```bash
  ps aux | grep sleep
  ```
  Untuk hasilnya  yaitu setelah proses  diberhentikan, tidak ada lagi proses `sleep` yang masih aktif.Hal ini membuktikan bahwa pada perintah `kill` berfungsi sangat efektif untuk mengontrol dan mengakhiri proses yang sedang bekerja.
  
  ---
- **Eksperimen 4 - Analisis Hierarki Proses**
  Pada percobaan ini atau yang terakhir menggunakan perintah:
  ```bash
  pstree -p | head-20
  ```
  Perintah ini akan menampilkan struktur hierarki proses kedalam bentuk pohon, di mana proses induk yang berada di atas dan proses anak berada di bawahnya.Hasilya dapat terlihat `systemd` sebagai proses induk utama (PID 1), dengan proses turunannya yait `bash,sleep`, dan yangg lainnya.Hal ini dapat menunjukan kalau setiap proses pada Linux mempunyai hubungan hierarki yang tersetruktr dariinduk ke anak.

  ---
     
## Analisis
1. Makna hasil percobaan.
   - Pembuatan user baru.
     Saat menjalankan perintah:
     ```bash
     sudo adduser praktikan
     ```
     Perintah tersebut menambahkan user baru bernama `praktikan`, dilengkapi dengan:
     - Home directory ``home/praktikan`.
     - Group utama `praktikan`
     - Password baru.
     - Informasi tambahan yang menunjukan cara Linux mengelola user dan group secara mandiri didalam sistem,seperti nama, nomor kamar, telepon, dll.
    - Menjalankan proses dan melihat proses.
      Pada saat menjalankan perintah:
      ```bash
      sleep 1000 &
      ```
      Proses `sleep` berjalan melewati background menggunakan PID (Process ID) = 729.Tanda beserta makna proses berjalan di background, tidak akan menghalangi terminal.
      Selanjutnya memeriksa proses:
      ```bash
      ps aux | grep sleep
      ```
      Pada perintah ini menampilkan semua proses dan menutupi yang mengandung kata `sleep`.Terlihat proses `sleep 1000`  beserta proses `grep` sendiri.
    - Eksperimen membunuh proses.
      Perintah yang menulis:
      ```bash
      kill <PID>
      ```
      Pada perintah ini terjadi eror syntax karena pengguna tidak mengganti `<PID>` dengan angka yang sesungguhnya, seperti `kill 729`.Apabila dilakukan, `kill 729` akan menghentikan proses `sleep 1000`.
    - Menampilkan pohon proses.
      Menjalankan perintah:
      ```bash
      pstree -p | head -20
      ```
      Perintah ini akan menampilkan hierarki proses yang lengkap dengan PID.Menunjukan hubungan parent-child process, yang berarti `systemd` adalah proses utama (PID 1), dan semua proses lain adalah turunannya.
    - Melihat aktivitas CPU dan memori.
      Menjalankan perintah:
      ```bash
      top
      ```
      Perintah ini akan menampilkan proses yang sedang bekerja, beberapa CPU dan RAM yang digunakan, siapa pemilik user-nya, dan status dari prosesnya.Misalnya proses `top` itu sendiri yang terlihat aktif `(%CPU 10.0)`.
      Makna dari keseluruhan:
      - Menunjukan bahwa kernel mengelola proses: setiap proses mempunyai PID, parent, dan child.
      - Dapat mengetahui kalu sistem dapat memantau dan mengendalikan proses menggunakan `ps`, `top`,  `pstree`, dan `kill`.
      - Menampilkan Linux mendukung multi-user dan multitasking dengan cara bersamaan.
  2. Hubungan hasill dengan teori(Kernel, System Call, dan Arsitektur OS)
     | No | Komponen Teori | Hungungan dengan Hasil Percobaan |
     |----|----------------|----------------------------------|
     | 1 | Kernel  | Kernel merupakan inti dari OS yang mempunyai tugas untuk mengatur proses, memori, I/O, dan manajemen user.Pada saat menjalankan perintah `sleep 1000`, kernel membuat Process Control Book baru pada memori dan mencatat didalam tabel proses. |
     | 2 | System Call | Pada saat menjalankan perintah ``sleep``, ``adduser``, dan ``kill``, perintah tersebut akan memanggil system call,seperti `fork()`, `exec()`, `exit()`, dan `kill`.Misalnya:`sleep 1000` - system call ``fork()`  akan membuat proses yang baru -  `exec()` dan mengganti isi proses menggunakan progam `sleep`. |
     | 3 | Arsitektur OS | OS dapat dibagi menjadi: User Space dan Kernel Space.Padda perintah yang dijalankan di shell `(bash)` berada di user space,tetapi eksekusinya dikerjakan oleh kernel.Komunikasi ini yang terjadi melalui system call interface. |
     | 4 | Proses dan Manajemen Proses | Untuk hasil `ps`, `top`, dan `pstree` menunjukan struktur hierarki proses,status (Running, Sleeping, Zombie), dan juga prioritas. Proses ini dapat membuktikan fungsi kernel dalam process scheduling dan resource management. |
3. Perbedaan hasil di lingkungan OS berbeda (Linux vs Windows).
   | No | Aspek | Linux | Windows |
   |---|--------|-------|---------|
   | 1 | Kernel dan arsitektur | Semua layanan utama dikerjakan di kernel space. | Hybrid kernel (gabungan dari microkernel dan monolithic).
   | 2 | Manajemen user dan grup | Proses ini menggunakan sistem user dan group yang berbasis file `etc/passwd,/etc/group`. | Menggunakan sistem akun yang berbasis registry dan domain (Active Directory). |
   | 3 | Perintah proses | `ps,top,pstree,kill,nice,renice`. | `tasklist,taskkill,taskmgr,wmic,process`. |
   | 4 | Tampilan proses | Text-based pada terminal, akan mudah diakses kalau melewati command line. | GUI-based di Task Manager, CLI opsional. |
   | 5 | Hierarki proses(parent-child) | Proses ini akan jelas terlihat lewat `ptree,systemd` yaitu parent utama. | Tidak akan selalu terlihat langsung; proses akan berdiri sendiri dalam GUI Task Manager. |
   | 6 | System call interface | POSIX standard | Win32 API (khusus Windows environment. |
   | 7 | Stabilitas dan kontrol | Administrator (`root`) memiliki kendali penuh pada sistem. | Administrator mempunyai kontrol yang lebih terbatas menggunakan UAC. |
---

## Kesimpulan
1. Sistem Linux dapat mengerjakan lebih banyak proses sekaligus dengan menggunakan struktur induk dan anak proses yang dapat diatur menggunakan nomor identitas pada proses (PID).
2. Kernel memiliki fungsi yang mengatur jalannya pada setiap proses di sistem,mulai dari pada saat embuat perangkat,menjalankan, sampai menghentikan proses dengan melalui mekanisme system call.
3. Linux dapat memberikan kebebasan dan kendali secara penuh untuk para pengguna yang memantau serta mengelola proses dengan menggunakan perintah, seperti `ps,top,pstree`, dan `kill`.

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
```
     systemd(1)
├─ agetty(186)
├─ agetty(191)
├─ cron(167)
├─ dbus-daemon(168)
├─ init-systemd(ub)(2)
│   └─ SessionLeader(548)
│       ├─ Relay(553)
│       │   ├─ head(733)
│       │   ├─ pstree(732)
│       │   └─ sleep(729)
│       ├─ init(7)
│       │   └─ init(8)
│       └─ login(314)
│           └─ bash(381)
├─ rsyslogd(193)
│   ├─ rsyslogd(223)
│   ├─ rsyslogd(224)
│   └─ rsyslogd(225)
├─ systemd(358)
│   └─ (sd-pam)(359)
├─ systemd-journal(53)
├─ systemd-logind(181)
├─ systemd-resolved(160)
├─ systemd-timesyncd(161)
│   └─ {systemd-timesyn}(165)
├─ systemd-udevd(97)
└─ unattended-upgr(202)
    └─ {unattended-upgr}(275)
```


    
 4.  Hubungan user management dan keamanan sistem Linux.
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
- Memahami dan menjalankan perintah Linux,karena saya masih ragu dengan jawaban dan hasil yang saya kerjakan. 
- Cara mengatasi dengan bertanya kepada teman.  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
