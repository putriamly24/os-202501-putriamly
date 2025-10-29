
# Laporan Praktikum Minggu Ke 3
Topik:  Penggunaan Perintah chmod dan chown dalam Mengelola Keamanan File dalam Sistem Operasi Linux.

---

## Identitas
- **Nama**  : Putri Amaliya Rahmadani
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Tujuan

Setelah menyelesaikan tugas ini, mahasiswa mampu:
1. Menggunakan perintah `ls`, `pwd`, `cd`, `cat` untuk navigasi file dan direktori.
2. Menggunakan `chmod` dan `chown` untuk manajemen hak akses file.
3. Menjelaskan hasil output dari perintah Linux dasar.
4. Menyusun laporan praktikum dengan struktur yang benar.
5. Mengunggah dokumentasi hasil ke Git Repository tepat waktu.


---

## Dasar Teori
1. Sistem Operasi Linux adalah suatu sistem opeasi berbasis Unix yang memiliki sifat terbuka dan telah banyak digunakan diberbagai proyek atau bidang.Linux menyiapkan lingkungan terminal yang memastikan para pengguna dapat berinteraksi langsung dengan sistem melewati perintah-perintah tertentu.
2. Hak akses (permission) memiliki fungsi yang dapat membatasi dann mengatur izin akses dalam mengerjakan suatu file atau folder.Pengaturan ini bertujuan untuk menjaga keamanan data pada sistem dan mencegah penyalahgunaan akses oleh pengguna lain.
3. Perintah `chmod` digunakan untuk mengatur izin akses file pada sistem operasi.Printah ini bertujuan agar pengguna dapat menggunakan hak akses baca,tulis,dan eksekusi untuk pemilik,grup,ataupun pengguna yang lain.
4. Perintah chown digunakan untuk mengganti kepemilikan file atau folder.Perintah ini bertujuan agar pengguna dapat mengatur izin akses pemilik dan grup dari dalam file supaya sesuai dengan kebutuhan sistem.
5. Kernel mempnyai peran sangat penting yaitu sebagai pengatur utama antara perangkat keras dan perangkat lunak.Saat perintah `chown` dan `chmod` dikerjakan,kernel akan memproses perintah melewati system call agar memastikan perubahan hak akses pada file dengan aman.

---

## Langkah Praktikum
1.**Setup Environment**

- Gunakan Linux (Ubuntu/WSL).
- Pastikan folder kerja berada di dalam direktori repositori Git praktikum:
```
praktikum/week3-linux-fs-permission/
```

2.**Eksperimen 1 – Navigasi Sistem File**
Jalankan perintah:
```bash

pwd
ls -l
cd /tmp
ls -a
```
- Jelaskan hasil tiap perintah.
- Catat direktori aktif, isi folder, dan file tersembunyi (jika ada).

3.**Eksperimen 2 – Membaca File** 
Jalankan perintah:
```bash

cat /etc/passwd | head -n 5
```
- Jelaskan isi file dan struktur barisnya (user, UID, GID, home, shell).

4.**Eksperimen 3 – Permission & Ownership** 
Buat file baru:
```bash

echo "Hello <NAME><NIM>" > percobaan.txt
ls -l percobaan.txt
chmod 600 percobaan.txt
ls -l percobaan.txt
```
- Analisis perbedaan sebelum dan sesudah chmod.
- Ubah pemilik file (jika memiliki izin sudo):
```bash
sudo chown root percobaan.txt
ls -l percobaan.txt
```
Catat hasilnya.

5.Eksperimen 4 – Dokumentasi

- Ambil screenshot hasil terminal dan simpan di:
```
praktikum/week3-linux-fs-permission/screenshots/
```
- Tambahkan analisis hasil pada `laporan.md`.

6.**Commit & Push**
```bash

git add .
git commit -m "Minggu 3 - Linux File System & Permission"
git push origin main
```


---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
pwd
ls -l
cd /tmp
ls -a

cat /etc/passwd | head -n 5

echo "Hello <NAME><NIM>" > percobaan.txt
ls -l percobaan.txt
chmod 600 perobaan.txt

sudo chown root percobaan.txt
ls -l percobaan.txt
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](<screenshots/eksperimen.putri.png>)
### Eksperimen 1

- **Perintah 1 :**
   | Perintah | output | Keterangan |
  | :--------| :-----| :--------|
  | ``pwd`` | ``/home/jimin`` | `pwd` (print working directory) Menampilkan lokasi direktori kerja saat difolder,artinya saat sedang berada di folder ``/home/jimin``atau direktori milik`jimin` |
- **Perintah 2 :**
  Perintah : `ls -l`

```bash
  -rw-r--r--  1  jimin  jimin  4096  Oct 25  13:32  percobaan.txt
```
- **Perintah 3 :**
   Perintah : `cd` /tmp

```bash

 ` cd` /tmp
```
Keterangan : Perintah `cd` (change directory)digunakan untuk berpindah direktori kerja,sedangkan direktori `/tmp` yaitu folder sementara (temporary directory) yang disediakan oleh sistem Linux untuk menyimpan file sementara.
Analisis : Ketika berpindah ke folder `/tmp` ,tempat umum buat mengerjakan eksperimen file tanpa mengganggu sistem utama.
- **Perintah 4 :**
  ```bash
  `ls -a`
  ```
  Keterangan :
  - Perintah `ls` digunakan untuk melihat isi direktori.
  - Opsi `-a` yaitu menunjukan semua file termasuk yang tersembunyi.
  - File maupun folder yang diawali tanda titik (.) adalah file tersembunyi.

## Eksperimen 2

```bash
  cat /etc/passwd | head -n 5
```
 Keterangan : 
1. `cat` (concatenate) digunakan untuk menampilkan isi file ke layar,dalam hal ini file file yang dibaca adalah `/etc/passwd` .
2. `|` (pipa) digunakan untuk mengarahkan output dari satu perintah menjadi input bagi perintah lain,dari hasilnya menjadi `cat /etc/passwd` dilanjutkan ke perintah selanjutnya ( `head -n 5` )
3. `head -n 5` menampilkan 5 baris pertama dari hasil input,yang bertujuan untuk tampilan tidak terlalu panjang,karena file `/etc/passwd` dapat berisi puluhan baris.

   Analisis Struktur Tiap Baris
   
 | No | Kolom               | Contoh      | Keterangan                                                               |
| -- | ------------------- | ----------- | ------------------------------------------------------------------------ |
| 1  | **Username**        | `root`      | Nama pengguna (`jimin`)                                               |
| 2  | **Password**        | `x`         | Menandakan password disimpan di file lain (`/etc/shadow`) untuk keamanan |
| 3  | **UID (User ID)**   | `0`         | Nomor unik identitas pengguna. UID 0 = root                              |
| 4  | **GID (Group ID)**  | `0`         | Nomor unik identitas grup utama pengguna                                 |
| 5  | **Comment / GECOS** | `root`      | Biasanya berisi nama lengkap pengguna atau deskripsi                     |
| 6  | **Home Directory**  | `/root`     | Folder utama pengguna                                                    |
| 7  | **Shell Login**     | `/bin/bash` | Program shell yang digunakan saat login (misal Bash atau nologin)        |

  Kesimpulan : Dari hasil eksperimen perintah `cat /etc/passwd | head -n 5`,didapatkan lima baris pertama dari file `/etc/passwd`yang berisi data akun pengguna dari dalam sistem.Setiap baris mempunyai struktur `username:x:UID:GID:komentar:home:shell`.Melewati percobaan ini dapat dipahami bahwa file `/etc/passwd` bertujuan untuk menyimpan identitas pengguna dan konfigurasi login pada sistem Linux.
  
   

            

  
  

---

## Analisis
1. Dari hasil percobaan menggunakan perintah ``ls-l``,``chmod``,dan ``chown``,dapat dilihat bagaimana proses Linux mengatur izin dan kepemilikan dari file.Perintah ``ls -l`` menunjukan pemilik dari file,grup,dan hak aksesnya ( ``rwx`` ).Setelah dikerjakan``chmod``,hak izin file akan berubah sesuai dengan nilai yang dikasihJika ``chown`` dikerjakan ,maka kepemilikan file juga aka langsung pindah ke user atau grup lain.
2. Pada sistem operasi ,kernel mempunyai tugas utama untuk mengatur semua akses ke perangkat keras serta file.Ketika mengetik perintah ``chmod`` atau ``chown``,perintah tersebut tidak langsung berubah file,melainkan mengirim permintaan (system call) ke kernel untuk dikerjakan.
   - Contohnya:
       - ``chmod``  menggunkan system call ``chmod()`` di kernel untuk mengubah permission file.
       - ``chown`` menggunakan system call``chown()`` untuk mengganti kepemilikan.
   - Arsitektur OS
       - Perintah dikerjakan mulai dari **user space** (melewati shell/terminal).
       -  Kernel mengeksekusi perubahan secara langsung di **kernel space**,yang mempunyai hak penuh kepada sistem file.
 3. Perbedaan hasil di OS (Linux vs Windows)
    | faktor | Linux | Windows |
    |--------|-------|---------|
    | Sistem izin (permission) | Memakai model ``rwx`` untuk owner,group,dan pengguna lain | Memakai sistem **Access Control** List (ACL) yang lebih detail. |
    | Perintah Control | Lewat terminal dengan ``chmod``,``chown``,``chgrp``(melalui terminal). | Biasanya melewati menu **Properties-Security**,atau pakai perintah ``icacls``. |
    | Kepemilikan file | Setiap file mempunyai satu pemilik dan satu grup utama. | File dapat dimiliki banyak user atau grup sekaligus dengan izin bebeda. |
    | Kernel dan system call | Gunakan system call POSIX seperti ``chmod()`` dan ``chown()``. | Gunakan API Windows seperti ``SetFileSecurity()``. |

---

## Kesimpulan
1. Perintah chmod digunakan untuk mengatur izin akses file yang digunakan,sedangkan perintah chown digunakan untuk mengubah pemilik atau grup dari file.
2. Proses perubahan izin serta kepemilikan yang dikerjakan oleh sistem agar menjaga keamanan dan pengatura pada file.
3. Linux menyediakan berbagai cara yang fleksibel dalam menjalankan hak akses melalui terminal,supaya pengguna lebih     mudah dalam menjalankan file dan foldernya.
   
---

## Tugas
Jelaska fungsi tiap perintah dan arti kolom permission (``rwxr--xr--``)
| No | Perintah | Fungsi | Hasil Observasi | 
|----|---------|--------|------------------|
| 1 | ``pwd`` | Menampilkan lokasi folder (direktori) yang aktif tempat pengguna sedang bekerja di terminal. | Menunjukan direktori bekerja secara aktif di folder ``/home/putri/Documents.`` |
| 2 | 



## Quiz
1.  Apa fungsi dari perintah chmod?
   **Jawaban :**
    Perintah chmod berfungsi untuk mengatur atau mengubah hak akses pada file ataupun folder didalam sistem operasi Linux atau 
              Unix.Lewat perintah ini,para pengguna dapat menentukan siapa saja yang dapat diperbolehkan membaca,mengedit,atau 
              mengerjakan file tersebut. 
3. Apa arti dari kode permission `rwxr-xr--`?
   **Jawaban:**
   Kode permission  ``rwxr-xr--`` artinya pemilik file mempunyai hak penuh untuk membaca,menulis,dan menjalankan file,sedangkan 
               grup hanya dapat membaca dan menjalankan,dan pengguna lain hanya dapat memiliki izin untuk membaca saja. 
5. Jelaskan perbedaan antara ``chown`` dan ``chmod``! 
   **Jawaban:**
   Perintah ``chown`` memiliki fungsi untuk mengganti siapa pemilik atau grup dari file atau folder,sedangkan perintah ``chmod``
               berfungsi untuk izin hak akses,yaitu siapa saja yang boleh membaca,menulis,atau menjalankan file.Jdipada intinya ``chown``
               mengatur kepemilikan terhadap file,sedangkan chmod mengtur hak akses terhadap file itu.  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
