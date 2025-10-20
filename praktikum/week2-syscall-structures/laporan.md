
# Laporan Praktikum Minggu [X]
Topik:Eksperimen Fungsi Kernel dan System Call dalam Mengatur Komunikasi Antara Aplikasi dan Hardware

---

## Identitas
- **Nama**  : PUTRI AMALIYA RAHMADANI  
- **NIM**   : 250202924
- **Kelas** : 1 IKRA

---

## Tujuan
-Menyadari pentingnya system call dalam menjaga keamanan progam dengan efisinsi dan stabilitas kerja dalam sistem operasi.
-Mengetahui peran penting kernel sebagai inti dari semua sistem operasi yang mengatur komunikasi antra perngkat keras dan perangkat 
 lunak.
-Dapat mengetahui bagaimana system call berfungsi sebagai perantara antara progam user dengan kernel.


---

## Dasar Teori
1.Kernel sebagai pusat sistem operasi
  Kernel bisa dikatakan sebagai bagian yang paling uatama dari sistem operasi yang menjalankan semua sumber daya di 
  komputer.Misalnya,mulai dari penggunaan CPU,memori,sampai perangkat-perangkat lainnya seperti  output/input semuanya diatur atau 
  dijalankan sama kernel agar sistem yang bekerja tetap stabil dan tidak saling mengganggu antar proses.
2.Peran system call dalam komunikasi progam dan kernel
  Progam yang dikerjakan oleh user sebenarnya tidak bisa langsung berinteraksi sama hardwar,alasannya disini karena system call jadi 
  penghubungnya.Melewati system call semua progam bisa meminta layanan ke kernel,contohnya buat baca file,menulis data,atau menjalankan 
  proses baru.Jadi system call ini semacam jembatan atau perantara antara progam user dan kernel. 
3.Alur kerja sistem operasi
  Di dalam sistem operasi mempunyai 2 mode utama:user mode dan kernel mode.Progam yang biasa jalan di user mode dengan hak akses 
  terbatas,sementara kernel jalan di kernel mode dengan akses penuh ke sistem proses ini sangat berbeda jauh dengan user mode.Jika 
  progam membutuhkan akses ke parangkat keras,progam bakal lewat system call terlebih dahulu baru dilanjutka ke kernel.Setelah semuanya 
  selesain akan dikembalikan lagi ke progam.
4.Keamanan dalam sistem operasi
  Perpindahan antara user mode dan kernel mode ini dibuat agar sistem yang dikerjakan lebih aman.Tujuannya agar progam tidak bisa 
  sembarangan masuk atau mengakses sumber daya yang penting.Dengan demikian,sistem operasi bisa dipastikan berjalan sesuai aturan tanpa 
  adanya sistem eror.
5.Perbedaan linux dan windows
  Walaupun fungsinya sama,cara bekerja di Linux dan Windows sedikit berbeda.Di Linux,semua prosesnya lebih terbuka dan masih bisa 
  dipantau pakai peintah strace.Sedangkan di Windows,lebih tertutup dan ketat karena melewati API,tapi inti dari keduanya tetap sama 
  yaitu menjadi penghubung antara user dan kernel agar progam bisa jalan secara efisisen.


---

## Langkah Praktikum
1. Buka terminal di sistem operasi Linux(ubuntu)buat memulai percobaan.
2. Jalankan perintah strace untuk melihat system  call apa saja yang dibutuhkan waktu progam dikerjakan.
3. Amati hasil keluarannya dan perhatikan urutan system call yang muncul diterminal.
4. Mencatat hasil dan analisis hubungan antara system call,kernel,dan cara kerja sistem operasi.    
5.Setelah semua data didapat,commit hasil percobaannya ke Git agar dokumentasinya rapi dan tersimmpan.   
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
- Makna Hasil Percobaan
  Untuk hasil percobaan yang telah dilakukan,bisa kita lihat kalau setiap progam yang dijalankan itu tidak langsung berinteraksi sama 
  hardware,melainkan harus melewati system call terebih dahulu.  
- Hubungan hasil dengan teori (fungsi kernel, system call, arsitektur OS).
  1.Fungsi Kernel
    Secara teori,kernel merupakan inti dari semua sistem operasi yang mengatur atau sebagai kunci sumber daya pada komputer.Dari 
    berbagai percobaan yang terlihat yaitu ketika kernel menerima system call dari user,mengerjakan semua prosesnya,dan dikembalikan 
    hasilnya ke progam.
  2.Peran System Call
    Teorinya,system call menjadi cara buat proses perpindahan dari user mode ke kernel mode.Untuk hasil pasti sesuai,karena progam yang 
    kita jalani pasti melewat tahap itu dulu sebelum mengaksses hardware.
  3.Arsitektur OS
    Berdasarkan teori yang menjelaskan alurnya:
    User Progam-System Call-Kernel-Hardware-Kembali lagi ke user progam,untuk alur ini sudah sesuai,karena prosesnya sama dengan yang 
    dikerjakn dengan konsep OS modern. 
-Perbedaan hasil di lingkungan OS berbeda (Linux vs Windows).
 Pada sistem operasi Linux,proses system call dapat dilihat dengan jelas,karena mempunyai sifat yang terbuka(open source).Linux yang menggunakan konsep system call bisa melacak penggunaan perintah seperti strace.Sedangkan pada windows menggunakan API untuk melakukan fungsi yang sama seperti pada halnya linux.Tetapi pada windows prosesnya lebih tertutup dan tidak mudal terlihat karena prose keamanannya lebih ketat dan aman.  

---

## Kesimpulan
1.System call itu merupakan bagian yang sangat penting pada sistem operasi,karena menjadi penghubung antara progam yang dikerjakan sama kernel.Lewat system call ini progam bisa meminta layanan dari sistem operasi secara aman dan terjaga keamanannya.
2.Keamanan sistem operasi juga banyak bergantung dengan system call,alasannya karena setiap pada saat perpndahan dari user mode ke kernel mode harus melewati mekanisme ini.Dengan demikian,sistem bisa mengecek dulu izin dan validitas akses.
3.Sistem call juga menjadi pelindung utama sistem operasi.Fungsiya dan tujuan bukan cuma buat mengatur permintaaan sistem tetapi juga keamanan dan performa sistem terjaga agar tetap aman.


   

## Tugas
1.Dokumentasi hasil eksperimen strace dan dmesg dalam bentuk tabel observasi


3.Analisis
System call sangat penting untuk melindungi keamanan kernel alasannya karena telah menyiapkan antarmuka yang terjaga dan dilindungi untuk semua akses yang ada di dalamnya.Kernel juga bisa mengatur dan memantau akses tersebut,serta dapat mencegah akses ilegal dan ancaman keamanan yang bisa membahayakan sistem dan rahasia dari data-data didalamnya,oleh karena itu system operasi bisa bekerja dengan aman tanpa gangguan dan ancaman pada sistem yang bekerja,serta dapat menjaga kepercayaan untuk para pengguna system operasi dan meminimalkan dampak negatif  pada operasional bisnis.System call juga dapat dikatakan sebagai "jantung komunikasi"antara para pengguna progam dan sistem operasi.Setiap kali kita atau para pengguna mengerjakan progam atau aturan-aturan di terminal,sebenarnya aplikasi itu tidak berhubungan secara langsung dengan perangkat-perangkat keras yang dapat membahayakan sistem.Semua data atau keinginan pengguna harus lewat sistem operasi,dan jalan yang digunakan yaitu system call.Contohnya ketika kita memulai untuk membuka file,nulis tes ke terminal yang disediakan ,atau mengakses jaringan pada suatu sistem didalamnya langkah nya semua hars lewat sysem call.Nah jadi dapat disismpulkan pula fungsi utama system call bukan sekedar"alat memanggil layanan OS",tetapi juga dapat mengatur,menjaga,atau memekanisme keamanan agar progam pengguna tidak sembarangan diotak-atik sistem.

Didalam sistem operasi modern,ada dua tipe kerja utama:yaitu antara lain ada user mode dan kernel mode.Di user mode,progam bekerja dengan hak untuk kebebasan suatu akses secara terbatas.Kalau mau di ibaratkan,ini kaya kehidupan sehari-hari manusia,yaitu kaya tamu dirumah orang lain  bisa memakai semua fasilitas di dalam rumah,tetapi kernel mode itu pemilik rumahnya ,mempunyai beberapa akses penuh terhadap sumber daya komputer,termasuk card sd,CPU,dan perangkat keras lainnya.Nah mungkin jika di dalam user mode bisa langsung masuk dan di utak-atik kernel,hasilnya bisa sangat fatal sistem didalamna bisa rusak,data rusak,dan keamanannya bisa terancam.

Maka dari itu,semua hubungan antara dari user mode ke kernel mode harus melewati system call.Contohnya,kaya saat aplikasi butuh untuk  membaca file,dia bakal meminta read().Tapi jika read()itu bukan beneran fungsi yang biasa,dia akan menimbulkan trap yang menubah mose CPU dari user mode ke kernel mode.Kernel lalu memantau dulu permintaanya,apakah boleh,apa alamat yang tertera valid dalam memori.Jika ada peringatan yang berbahaya atau yang tidak diperbolehkan,maka kernel aka menolak semua permintaan tersebut untuk melindungi keamanan progam tersebut dari berbagai kerusakan yang mengancam keamanan pada sistem.

Dengan cara ini system call tidak hanya berfungsi sebagai alat penghubung,melainkan dapat menjadi suatu lapisan pelindung utama(security layer) yang melindungi agar suatu aplikasi atau progam para pengguna tidak dapat asal masuk kedalam sisem secara lagsung atau tatapmuka.Melalui berbagai penjagaaan yang ketat ,sistem operasi dapat berjalan dengan stabil dan aman,juga tidak perlu dihawatirkan lagi untuk kepercayaaan para pengguna sistem operasi.

System call juga menjadi solusi atau tujuan suatu progam untuk mencegah berbagai hal yang tidak diinginkan,dengan adanya penyediaan penggunaan antarmuka untuk mengerjakan suatu progam bagi para pengguna sistem operasi pemintaan akses pada sumber daya harus berjalan dengan melalui kernel,yang akan memeriksa dan memastikan beberapa tindakan dengan aman .Hal ini sangat penting adanya untuk penggunaan sistem operasi multi-user,dimana beberapa pengguna sistem operasi dapat menyelesaikan proses dengan bersamaan teteapi tetap melakukan pembatasan agar tidak saling mengganggu atau mengakses data satu sama lain. 

Dengan demikian,dapat disimpulkan bahwa system call adalah elemen vital dalam desain keamanan sistem operasi.Ia memastikan bahwa semua penghubung antara lain aplikasi atau progam,kernel,dan perangkat keras berlangsung terkontrol,dan terlindungi dari berbagai ancaman yang dapat mengganggu kinerja ataupun keamanan pada sistem secara menyeluruh.


## Quiz
1. Pertanyaan: Apa fungsi utama system call dalam system operasi?  
   Jawaban   : Fungsi utama system call yaitu jadi perantara antara suatu progam yang kita kerjakan sama sistem operasi.
               Dengan tidak adanya system call,sistem biasa tidak bisa berhubungan secara langsung sumber daya dari sistem karena 
               keamanan dan stabilitasnya kurang memenuhi. 
2. Pertanyaan: Sebutkan 4 kategori system call yang umum digunakan!
   Jawaban   : Process control,file management,information maintenance,device management.      
3. Pertanyaan: Mengapa system call tidak bisa dipanggil langsung oleh user progam? 
   Jawaban   : Alasannya karena progam bekerja di user mode sedangkan system call dikerjakan dikernel mode,jika dijalankan secara paksa 
               maka data-data didalamnya bisa rusak dan keamanan sistem terancam. 

---

## Refleksi Diri
Tuliskan secara singkat:
- Bagian yang paling menantang saya dalam minggu ini yaitu fokus mengerjakan beberapa tugas kuliah,salah satunya tugas matkul sistem 
  operasi,yaitu memahami konsep system call dan peran kernel karena materinya cukup sulit bagi saya untuk dipahami.   
- Cara saya mengatasinya dengan cara bertanya dan berdiskusi dengan teman,santai dulu-main sebentar,makan seblak biar fresh,baru lanjut 
  ngerjain tugas hihihi.  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
