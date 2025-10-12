
# Laporan Praktikum Minggu [X]
Topik: Arsitektur dan Fungsi Kernel dalam Sistem Operasi Modern 

---

## Identitas
- Nama  : PUTRI AMALIYA RAHMADANI 
- NIM   : 250202924
- Kelas : 1IKRA 

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
- Mampu menganalisis arsitektur dan fungsi kernel dalam sistem operasi modern.
- Mahasiswa dapat membandingkan kelebihan dan kekurangan jenis kernel dalam sistem operasi.
- Mahasiswa dapat memahami prinsip-prinsip dasar arsitektur.
---

## Dasar Teori
1.Sistem Operasi, Apa Sih Itu?: Sistem operasi adalah semacam "otak" komputer yang ngatur semua sumber daya dan perangkat keras, supaya semuanya bisa berjalan lancar dan sesuai dengan yang kita mau, sistem operasi juga mengatur antara perangkat keras dan perangkat lunak,serta menyediakan antarmuka bagi pengguna untuk pengoperasian komputer.
2.Fungsi Utama Sistem Operasi: Sistem operasi memiliki beberapa fungsi krusial, yaitu manajemen proses yang mengatur program yang berjalan, manajemen memori yang mengoptimalkan penggunaan memori, manajemen file yang mengatur penyimpanan dan akses file, serta manajemen input/output yang mengatur interaksi dengan perangkat input dan output.
3.Pilihan Sistem Operasi: Ada dua jenis sistem operasi yang populer, yaitu sistem operasi open-source yang memberikan kita kebebasan untuk mengrubah dan mengembangkan sesuai kebutuhan, dan sistem operasi komersial yang menawarkan kemudahan penggunaan dan dukungan teknis yang baik.
4.Kelebihan dan Kekurangan: Setiap sistem operasi punya kelebihan dan kekurangan masing-masing, tergantung dari kebutuhan dan preferensi kita. Sistem operasi open-source menawarkan fleksibilitas, sedangkan sistem operasi komersial menawarkan kemudahan dalam penggunaan.
5.Memilih Sistem Operasi yang Tepat: Memilih sistem operasi yang sesuai dengan kebutuhan kita sangat penting, supaya kita bisa bekerja dengan lebih efisien dan produktif. Jadi, kita perlu mempertimbangkan apa yang kita butuhkan dari sistem operasi sebelum membuat berbagai keputusan.

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
![alt text](<screenshots/ss putri.png>)

---

## Analisis 
- `uname -a`: Menampilkan informasi sistem secara lengkap, termasuk nama kernel, versi, dan arsitektur sistem.
- `whoami`: Menampilkan nama pengguna yang saat ini login. Untuk menampilkan semua pengguna yang login, bisa menggunakan perintah `who` atau `users`.
- `lsmod | head`: Menampilkan daftar modul kernel aktif yang dimuat pada sistem, dengan "head" menampilkan 10 baris pertama dari daftar tersebut.
- `dmesg | head`: Menampilkan pesan-pesan boot sistem dan deteksi perangkat keras, dengan "head" menampilkan 10 pesan pertama.
- Kaitan antara hasil dengan teori kernel,panggilan sistem(system call) dan arsitektur sistem operasi:Dengan demikian, kode-kode tersebut menunjukkan bagaimana system call menjadi jembatan antara pengguna dan kernel, serta menggarisbawahi peran krusial kernel dalam mengoptimalkan pengelolaan sumber daya sistem dan penyediaan informasi sistem yang akurat, yang merupakan fondasi utama dalam teori sistem operasi.
- Perbedaan hasil dalam lingkungan OS (Linux vs Windows):Perbedaan antara Linux dan Windows yang mencolok dalam berbagai aspek, seperti format file sistem, antarmuka pengguna, dan manajemen keamanan, merupakan hasil dari perbedaan fundamental dalam arsitektur, tujuan pengembangan, dan filosofi yang dianut oleh kedua sistem operasi tersebut.


## Kesimpulan
• Pilihan yang Tepat: Saya menyadari bahwa memilih platform komputasi yang tepat sangat penting untuk mengoptimalkan kinerja dan produktivitas, dan setiap sistem memiliki kelebihan dan kekurangan yang perlu dipertimbangkan.
• Kelebihan yang Berbeda: Menurut pengalaman saya, sistem operasi open-source menawarkan fleksibilitas dan kontrol yang sangat berguna untuk pengembangan dan kebutuhan teknis, sedangkan sistem operasi komersial unggul dalam kemudahan penggunaan dan kompatibilitas aplikasi.
• Pengambilan Keputusan yang Bijak: Dengan memahami perbedaan antara kedua sistem operasi tersebut, saya dapat membuat keputusan yang lebih tepat dan sesuai dengan kebutuhan saya, sehingga meningkatkan efisiensi dan produktivitas dalam penggunaan teknologi.


## Quiz
1. Pertanyaan:Sebutkan tiga fungsi utama sistem operasi.
   Jawaban   :Mengelola sumber daya, mengatur proses, mengatur data dan penyimpanan 
2. Pertanyaan:Jelaskan perbedaan anatara kernel mode dan user mode.
   Jawaban   :Kernel Mode memberikan kontrol penuh atas sistem dan perangkat kerasnya, sementara User Mode beroperasi                   dengan akses terbatas untuk memastikan keamanan, stabilitas, dan integritas sistem secara keseluruhan.
3. Pertanyaan:Sebutkan contoh OS dengan arsitektur monolithic dan microkernel.
   Jawaban   :Contoh sistem operasi arsitektur monolithic yaitu Linux dan Windows, sedangkan contoh sistem operasi dengan               arsitektur mikro-kernel yaitu QNX dan MINIX.


## Refleksi Diri
Tuliskan secara singkat:
- Pengalaman menantang bagi saya adalah ketika harus memahami konsep sistem operasi sebagai mahasiswa baru di ilmu komputer, karena masih perlu waktu untuk memahami bahasa dan terminologi teknis yang masih kurang familiar.
- Cara saya mengatasinya yaitu dengan mencari sumber belajar tambahan seperti buku dan video tutorial yang membahas tentang sistem operasi, serta berdiskusi dengan teman yang mungkin lebih memahami.

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
