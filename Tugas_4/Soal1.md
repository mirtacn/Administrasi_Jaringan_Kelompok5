 <h1 align="Center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1> 




<p align="center">
  <img src="img/Logo_PENS.png" alt="Logo PENS">
</p>



<p align="center">
Arsyita Devanaya Arianto (3122500008) <br>

</p>

<br>
<h4 align="center">
PROGRAM STUDI VOKASI <br>
D-III TEKNIK INFORMATIKA <br>
DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER 
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br> 
2023
</h4> <br><br><hr>

# Ekosistem Internet
Internet berkembang pesat di seluruh dunia berkat kepemilikan global bersama, pengembangan standar terbuka, dan proses pengembangan teknologi dan kebijakan yang dapat diakses secara bebas. Keberhasilan Internet didorong oleh model yang terbuka, transparan, dan kolaboratif.

<hr>

<p align="center">
  <img src="img/gambar_1.png" alt="Ekosistem internet">
</p>

## 2 Sudut Pandang Internet

- Teknis
  - Routing System(system routing)
  - Naming system(sistem penamaan)
- Arsitektur
  - Standars(standarsiasi)
  - Service Provider(Penyedia layanan)
  - Internet Registries(Internet register)
  - Clearing Houses(Rumah kliring)
<hr>

### IP Addressing & Routing System
Perutean internet adalah proses pengalihan lalu lintas dari berbagai jaringan yang melibatkan pengambilan paket data dari satu titik ke titik tujuan melalui serangkaian perangkat jaringan dan rute yang optimal.

1. Perutean dimulai dari pengguna atau pelanggan internet yang ingin mengakses konten atau layanan online. Mereka terhubung ke penyedia layanan internet (ISP) atau operator jaringan untuk mendapatkan akses ke internet.
2. Internet Protocol (IP) adalah protokol yang digunakan untuk mengirim dan menerima data di internet. Setiap perangkat yang terhubung ke internet diberikan alamat IP yang unik.
3. Data yang dikirim melalui internet dibagi menjadi paket-paket kecil sebelum dikirim. Setiap paket memiliki header yang berisi informasi tentang asal, tujuan, dan urutan paket dalam pesan.
4. Sistem perutean internet mengarahkan paket data melalui jaringan dengan menggunakan perangkat keras dan perangkat lunak khusus yang disebut router.
5. Router menggunakan tabel rute yang diperbarui secara dinamis untuk menentukan jalur terbaik untuk mengirim paket dari sumber ke tujuan.
6. Ada berbagai algoritma perutean yang digunakan untuk menentukan jalur terbaik untuk mengirim data. Algoritma-algoritma ini mempertimbangkan faktor-faktor seperti jarak, kecepatan, keandalan, dan beban lalu lintas pada jaringan.
7. Protokol-perprotokol seperti Border Gateway Protocol (BGP) dan Open Shortest Path First (OSPF) digunakan oleh router untuk berkomunikasi satu sama lain dan bertukar informasi tentang topologi jaringan.
8. Penyedia layanan internet dapat menghubungkan jaringan mereka melalui peering langsung atau menggunakan layanan transit dari penyedia jaringan lain untuk mencapai destinasi yang tidak terhubung secara langsung.
9.  IXPs adalah tempat di mana penyedia layanan internet dapat bertukar lalu lintas mereka secara lokal, mengurangi ketergantungan pada jalur luar yang lebih lambat.
10. Beberapa router menyimpan salinan data yang sering diakses dalam cache untuk mengurangi waktu respon dan mengoptimalkan penggunaan bandwidth.
11. Setelah melewati serangkaian router dan jaringan, paket data mencapai tujuan akhir dan diproses oleh komputer atau perangkat yang dimaksudkan.

<hr>

### Naming System
Sistem penamaan internet adalah bagian dari bagaimana alamat internet dikenali dan diakses oleh pengguna. Berikut adalah detail tentang bagaimana sistem penamaan internet berfungsi:

1. DNS adalah sistem penerjemah nama domain yang mudah diingat menjadi alamat IP numerik unik yang diperlukan perangkat untuk berkomunikasi di internet.

2. Sistem penamaan internet dibagi menjadi hierarki domain yang terdiri dari beberapa tingkat, mulai dari TLD (Top-Level Domain) hingga subdomain dan nama host. Contohnya adalah ".com", ".org", ".net" untuk TLD.

3. FQDN (Fully Qualified Domain Name) adalah representasi lengkap dari nama domain, yang mencakup semua tingkat domain mulai dari TLD hingga nama host. Sebagai contoh, "www.google.com" adalah FQDN.

4. Namespace DNS adalah ruang nama di mana semua nama domain dan subdomain berada. Setiap domain memiliki namespace yang terkait dengannya.

5. Server nama adalah server yang menyimpan catatan DNS dari klien dan memberikan jawaban yang sesuai, seperti alamat IP yang terkait dengan nama domain yang diminta.

6. Tautan DNS adalah koneksi antara domain dan alamat IP yang menyimpan informasi tentang lokasi fisik server yang meng-host domain tersebut.

7. Catatan DNS adalah informasi yang disimpan dalam server nama dan mencakup informasi tentang domain, seperti alamat IP yang terkait, server email, server nama, dan sebagainya.

8. NS beroperasi menggunakan protokol komunikasi khusus yang memungkinkan pengiriman permintaan dan respon antara server nama dan klien DNS. Protokol ini menggunakan format pesan standar dan menggunakan port 53 untuk komunikasi.

9. Operasi DNS terdiri dari proses penyebaran informasi, caching, pencarian, dan pembaruan yang terjadi ketika klien DNS meminta informasi tentang sebuah domain.

10. Resolusi DNS adalah proses di mana server nama menemukan dan mengembalikan alamat IP yang terkait dengan nama domain yang diminta oleh klien DNS.

Dengan sistem penamaan internet yang kompleks dan efisien, pengguna dapat dengan mudah mengakses situs web dan layanan online hanya dengan mengingat nama domain yang mudah diingat tanpa harus mengingat alamat IP yang rumit.

<hr>

### Standars

Standarisasi internet adalah proses di mana standar teknis dan protokol digunakan untuk memastikan interoperabilitas dan kompatibilitas antara perangkat dan layanan yang beroperasi di internet. 

Beberapa organisasi standar utama yang terlibat dalam standarisasi internet meliputi : 
1. Internet Engineering Task Force (IETF) :  Semua protokol transport dan routing lapisan 3, termasuk IP, TCP, UDP, HTTP, DNS, protokol perutean, telnet, rsync, IPsec, dan protokol manajemen jaringan.
2. Institute of Electrical and Electronics Engineers (IEE): Semua protokol bidang transportasi dan kontrol lapisan 1 dan lapisan 2, termasuk Ethernet, spanning tree, tongkat jaringan tanpa kabel.
3. World Wide Web Consortium (W3C) : Bahasa markup (bahasa yang menjelaskan cara menampilkan atau merender
konten), termasuk HTML dan XML
4. International Telecommunication Union (ITU) : Standar Internasional apa pun, termasuk penomoran, skema enkripsi, dan protokol perutean (seperti IS-IS)

<hr>

### Service Provider
Penyedia Layanan Internet (Internet Service Provider/ISP) adalah perusahaan atau organisasi yang menyediakan layanan akses internet kepada pengguna akhir atau organisasi. Berikut adalah beberapa aspek detail tentang penyedia layanan internet:
1. Penyedia Konten
   Penyedia konten ini terdiri dari pembuatan dan distribusi media yang menghubungkan pembeli dan penjual jasa/hiburan. Contoh: amazon, microsoft, google, Extrade, netflix, dan mercado libre.
2. Penyedia Akses
   Menyediakan koneksi internet bagi pengguna individu, bisnis, dan organisasi. Juga sering terlibat dalam pembuatan dan distribusi konten. Contoh: verizon, indosat ooredoo, indihome, comcast, directy, dan road runner.
3. Penyedia Transportasi Umum
   Menyediakan interkoneksi antar penyedia konten dan akses. Contoh: Duta Utama Net, Equinix, Telkom digital Solution,dan Indosat ooredoo.
4. Titik Pertukaran internet
   Menyediakan interkoneksi lokal untuk penyedia akses dan konten. Contoh openixp, Linx, dan Hurricane Electric.

<hr>

### Internet Registries

Internet registries adalah lembaga yang bertanggung jawab untuk mengatur dan mengelola sumber daya internet, terutama dalam hal alamat IP dan nama domain. Berikut adalah penjelasan detail tentang internet registries:

1. Internet Assigned Numbers Authority (IANA)
   IANA adalah otoritas pusat yang mengoordinasikan penetapan nomor dan nama yang membuat internet berfungsi.
2. Regional Internet Registries (RIRs)
   RIRs adalah organisasi non-profit yang mengelolan penetapan blok alamat ip untuk satu wilayah, berpartisipasi dalam penelitian, dan upaya standarsiasi.
3. American Registry for Internet Numbers (ARIN)
   Menangani alokasi alamat IP di Amerika Utara, Amerika Latin, dan Karibia.

<hr>

### Clearing Houses

Clearing house dalam konteks internet adalah lembaga yang memfasilitasi pertukaran lalu lintas data dan peering antara penyedia layanan internet (ISP), penyedia konten, dan penyedia jaringan lainnya. Mereka juga membantu dalam penyelesaian biaya pertukaran lalu lintas dan negosiasi kesepakatan peering. Dengan demikian, clearing house berperan penting dalam menjaga infrastruktur internet yang berkelanjutan dan efisien, serta membangun ekosistem internet yang sehat.
