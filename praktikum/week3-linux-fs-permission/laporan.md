
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
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](<screenshots/eksperimen.putri.png>)

---

## Analisis
 Dari hasil percobaan yang dikerjakan,perintah chmod dan chown berfungsi untuk mengatur keamanan serta hak akses file didalam sistem operasi Linux.Perintah chmod digunakan untuk mengubah izin agar pengguna bisa mengakses dan menjalankan file sesuai keinginannya,sedangkan chown berfungsi mengganti pemilik atau grup dari file tersebut.Jika perintah ni dikerjakan,maka sistem akan memanggil system call ke kernel untuk menerapkan perubahan pada file.
 Hasil tersebut menunjukan bahwa kernel memiliki peran dan fungsi yang sangat penting sebagai penghubung antara pengguna dan perangkat keras,terutama pada saat mengatur akses terhadap file supaya sistem tetap aman.Proses system call juga memastikan kalau setiap perintah dikerjakan didalam mode kernel tanpa melanggar batas akses pengaturan sistem.
 Jika dibandingkan perbedaan dengan Windows,Linux lebih fleksibel karena pengaturan izin dan kepemilikan file dapat dikerjakan secara langsung lewat terminal menggunakan chmod dan chown.Sedangkan,di Windows pengatura izin dilakukan melalui menu properti file,dan tidak semua pengaturan dapat diubah secara langsung melalui command prompt.

---

## Kesimpulan
1. Perintah chmod digunakan untuk mengatur izin akses file yang digunakan,sedangkan perintah chown digunakan untuk mengubah pemilik atau grup dari file.
2. Proses perubahan izin serta kepemilikan yang dikerjakan oleh sistem agar menjaga keamanan dan pengatura pada file.
3. Linux menyediakan berbagai cara yang fleksibel dalam menjalankan hak akses melalui terminal,supaya pengguna lebih     mudah dalam menjalankan file dan foldernya.

---

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
5. Jelaskan perbedaan antara chown dan chmod! 
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
