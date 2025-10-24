
# Laporan Praktikum Minggu Ke 3
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Putri Amaliya Rahmadani
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

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
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

## Quiz
1. Pertanyaan: Apa fungsi dari perintah chmod?
   Jawaban  : Perintah chmod berfungsi untuk mengatur atau mengubah hak akses pada file ataupun folder didalam sistem operasi Linux atau 
              Unix.Lewat perintah ini,para pengguna dapat menentukan siapa saja yang dapat diperbolehkan membaca,mengedit,atau 
              mengerjakan file tersebut. 
2. Pertanyaan: Apa arti dari kode permission rwxr-xr--?
   Jawaban   : Kode permission  rwxr-xr-- artinya pemilik file mempunyai hak penuh untuk membaca,menulis,dan menjalankan file,sedangkan 
               grup hanya dapat membaca dan menjalankan,dan pengguna lain hanya dapat memiliki izin untuk membaca saja. 
3. Pertanyaan: Jelaskan perbedaan antara chown dan chmod! 
   Jawaban   : Perintah chown memiliki fungsi untuk mengganti siapa pemilik atau grup dari file atau folder,sedangkan perintah chmod 
               berfungsi untuk izin hak akses,yaitu siapa saja yang boleh membaca,menulis,atau menjalankan file.Jdipada intinya chown 
               mengatur kepemilikan terhadap file,sedangkan chmod mengtur hak akses terhadap file itu.  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
