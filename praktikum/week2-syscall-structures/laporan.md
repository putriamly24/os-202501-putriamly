
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : PUTRI AMALIYA RAHMADANI  
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
![Screenshot hasil](<screenshots/stracels1.png>)
![Screenshot hasil](<screenshots/stracels2.png>)
![Screenshot hasil](<screenshots/stracels3.png>)
![Screenshot hasil](<screenshots/strace-e.png>)
![Screenshot hasil](<screenshots/dmesg.png>)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
1.System call itu merupakan bagian yang penting banget pada sistem operasi,karena menjadi penghubung antara progam yang dikerjakan sama kernel.Lewt system call ini progam bisa meminta layanan dari sistem operasi secara aman dan terjaga keamanannya.
2.Keamanan sistem operasi juga banyak bergantung sama dengan system call,alasannya karena setiap pada saat perpndahan dari usr mode ke kernel mode harus melewati meknisme ini.Dengan demikian,sistem bis mengecek dulu izizn dan vaaliditas akses.
3.Sistem call juga menjddi pelindung utama sistem operasi.Fungsiya dan tujuan bukan cuma buat mengatur permintaaan sistem tetapi juga keamanan dan performa sistem terjaga agar teetaap aman.

---
## Tugas
3.Analisis
System call sangat penting untuk melindungi keamanan kernel alasannya karena telah menyiapkan antarmuka yang terjaga dan dilindungi untuk semua akses yang ada didalamnya.Kernel juga bisa mengatur dan memantau akses tersebut,serta dapat mencegah akses ilegal dan ancaman keamanan yang bisa membahayakan sistem dan rahasia dari data-data didalamnya,oleh karena itu system operasi bisa bekerja dengan aman tanpa gangguan dan ancaman pada sistem yang bekerja,serta dapat menjaga kepercayaan untuk para pengguna system operasi dan meminimalkan dampak negatif  pada operasional bisnis.System call juga dapat dikatakan sebagai "JANTUNG KOMUNIKASI"antara para pengguna progam dan sistem operasi.Setiap kali kita atau para pengguna mengerjakan progam atau aturan-aturan di terminal,sebenarnya aplikasi itu tidak berhubungan secara langsung dengan perangkat-perangkat keras yang dapat membahayakan sistem.Semua data atau keinginan pengguna harus lewat sistem operasi,dan jalan yang digunakan yaitu system call.Contohnya ketika kita memulai untuk membuka file,nulis tes ke terminal yang disediakan ,atau mengakses jaringan pada suatu sistem didalamnya langkah nya semua hars lewat sysem call.Nah jadi dapat disismpulkan pula fungsi utama system call bukan sekedar"alat memanggil layanan OS",tetapi juga dapat mengatur,menjaga,atau memekanisme keamanan agar progam pengguna tidak sembarangan diotak-atik sistem.

Didalam sistem operasi modern,ada dua tipe kerja utama:yaitu antara lain ada user mode dan kernel mode.Di user mode,progam bekerja dengan hak untuk kebebasan suatu akses secara terbatas.Kalau mau di ibaratkan,ini kaya kehidupan sehari-hari manusia,yaitu kaya tamu dirumah orang lain  bisa memakai semua fasilitas di dalam rumah,tetapi kernel mode itu pemilik rumahnya ,mempunyai beberapa akses penuh terhadap sumber daya komputer,termasuk card sd,CPU,dan perangkat keras lainnya.Nah mungkin jika di dalam user mode bisa langsung masuk dan di utak-atik kernel,hasilnya bisa sangat fatal sistem didalamna bisa rusak,data rusak,dan keamanannya bisa terancam.

Maka dari itu,semua hubungan antara dari user mode ke kernel mode harus melewati system call.Contohnya,kaya saat aplikasi butuh untuk  membaca file,dia bakal meminta read().Tapi jika read()itu bukan beneran fungsi yang biasa,dia akan menimbulkan trap yang menubah mose CPU dari user mode ke kernel mode.Kernel lalu memantau dulu permintaanya,apakah boleh,apa alamat yang tertera valid dalam memori.Jika ada peringatan yang berbahaya atau yang tidak diperbolehkan,maka kernel aka menolak semua permintaan tersebut untuk melindungi keamanan progam tersebut dari berbagai kerusakan yang mengancam keamanan pada sistem.

Dengan cara ini system call tidak hanya berfungsi sebagai alat penghubung,melainkan dapat menjadi suatu lapisan pelindung utama(security layer) yang melindungi agar suatu aplikasi atau progam para pengguna tidak dapat asal masuk kedalam sisem secara lagsung atau tatapmuka.Melalui berbagai penjagaaan yang ketat ,sistem operasi dapat berjalan dengan stabil dan aman,juga tidak perlu dihawatirkan lagi untuk kepercayaaan para pengguna sistem operasi.

System call juga menjadi solusi atau tujuan suatu progam untuk mencegah berbagai hal yang tidak diinginkan,dengan adanya penyediaan penggunaan antarmuka untuk mengerjakan suatu progam bagi para pengguna sistem operasi pemintaan akses pada sumber daya harus berjalan dengan melalui kernel,yang akan memeriksa dan memastikan beberapa tindakan dengan aman .Hal ini sangat penting adanya untuk penggunaan sistem operasi multi-user,dimana beberapa pengguna sistem operasi dapat menyelesaikan proses dengan bersamaan teteapi tetap melakukan pembatasan agar tidak saling mengganggu atau mengakses data satu sama lain. 

Dengan demikian,dapat disimpulkan bahwa system call adalah elemen vital dalam desain keamanan sistem operasi.Ia memastikan bahwa semua penghubung antara lain aplikasi atau progam,kernel,dan perangkat keras berlangsung terkontrol,dan terlindungi dari berbagai ancaman yang dapat mengganggu kinerja ataupun keamanan pada sistem secara menyeluruh.


## Quiz
1. Pertanyaan: Apa fungsi utama system call dalam system operasi?  
   Jawaban   : Fungsi utama system call yaitu jadi perantara antara suatu progam yang kita kerjakan sama sistem operasi.
               Dengan tidak adanya system call,sistem biasa tidak bisa berhubungan secara langsung sumber daya dari sistem karena keamanan                dan stabilitasnya kurang memenuhi. 
3. Pertanyaan: Sebutkan 4 kategori system call yang umum digunakan!
   Jawaban   : Process control,file management,information maintenance,device management.      
4. Pertanyaan: Mengapa system call tidak bisa dipanggil langsung oleh user progam? 
   Jawaban   : Alasannya karena progam bekerja di user mode sedangkan system call dikerjakan dikernel mode,jika dijalankan secara paksa maka data-data didalamnya bisa rusak dan keamanan sistem terancam. 

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
