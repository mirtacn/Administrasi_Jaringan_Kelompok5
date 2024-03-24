 <h1 align="Center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1> 

<p align="center">
  <img src="img/Logo_PENS.png" alt="Logo PENS">
</p>

<p align="center">
Mirta Chadhirotin Nachlah <br>
(3122500009) <br>
2 D3 IT A

<p>
<h4 align="center">
PROGRAM STUDI VOKASI <br>
D-III TEKNIK INFORMATIKA <br>
DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER 
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br> 
2024
</h4> <br><br><hr>


## Ekosistem Internet     

Tugas Baca tentang Ekosistem Internet (Materi sudah diunggah di Ethol). Tuliskan pendapatmu tentang bagaimana Internet bekerja (tugas pribadi)!

Internet adalah sebuah ekosistem yang kompleks yang melibatkan berbagai entitas & protokol untuk berfungsi dengan baik. Internet bekerja dengan cara mentransmisikan data dan informasi antara jutaan komputer yang terhubung di seluruh dunia. Data dikirim dalam bentuk paket melalui serangkaian koneksi dan jaringan yang kompleks.

Beberapa komponen utama yang memungkinkan internet bekerja adalah:
- Internet service provider (ISP) : Perusahaan yang menyediakan koneksi internet ke perangkat pengguna . Contoh: Telkomsel, Indosat, XL.
- Protokol TCP/IP: Standar komunikasi yang memungkinkan pertukaran data antar jaringan komputer yang berbeda. TCP mengatur koneksi dan IP untuk menentukan alamat tujuan.
- Router: Perangkat yang menghubungkan jaringan lokal dengan internet global dan meneruskan data ke tujuannya. Sistem routing memastikan bahwa informasi mencapai tujuannya melalui serangkaian router, dengan setiap router memiliki alamat IP. Ada dua jenis alamat IP, yaitu: IPv4 dan IPv6. 
- Server: Komputer yang menyimpan, memproses, dan memberikan data atau layanan yang diminta oleh client/pengguna.
- HTTP & HTTPS: Protokol yang memungkinkan pertukaran data & informasi client-server, seperti browser-website.

Prosesnya dimulai ketika pengguna mengakses internet via koneksi lokal (kabel/WiFi) menuju router, lalu router meneruskannya ke ISP. ISP kemudian mentransmisikan data lewat berbagai jaringan hingga sampai ke server tujuan. Server memproses permintaan dan mengirimkan respons kembali ke pengguna.

penyedia konten seperti Google dan YouTube memiliki kebijakan routing sendiri untuk mengelola dan mengoptimalkan pengiriman konten kepada pengguna mereka. Salah satunya adalah pemberian cache, di mana konten yang sering diminta disimpan di server cache yang tersebar di seluruh jaringan mereka. Ini membantu mempercepat akses konten dan meningkatkan kepuasan pengguna dengan mengurangi waktu muat.

### DNS (Domain Name System) 
sistem yang memungkinkan pengguna untuk mengakses situs web menggunakan nama domain alih-alih alamat IP. Ini melibatkan hirarki server DNS yang terdiri dari nameserver dan resolver. Ketika pengguna memasukkan nama domain ke dalam peramban, resolver bertanggung jawab untuk mencari alamat IP terkait dengan nama domain tersebut melalui proses yang melibatkan nameserver.

### Standardisasi Internet
IETF (Internet Engineering Task Force) adalah badan standar yang bertanggung jawab atas standarisasi teknis dalam pengembangan internet. Mereka mengembangkan protokol untuk berbagai lapisan internet, termasuk protokol pada layer 3 transport (seperti TCP dan UDP) dan protokol lainnya yang mendasari fungsi jaringan dan komunikasi data. Standarisasi oleh IETF membantu memastikan interoperabilitas dan kompatibilitas antara berbagai perangkat dan jaringan di seluruh dunia.

Dengan kerja sama dan interaksi antara semua komponen ini, Internet dapat berfungsi sebagai jaringan global yang terbuka, transparan, dan kolaboratif yang memungkinkan pertukaran informasi dan komunikasi di seluruh dunia.

<br>

#### Berikut adalah rangkuman dari materi ekosistem internet :

# Ekosistem Internet
Internet berkembang pesat di seluruh dunia karena tiga kunci sukses: kepemilikan global bersama, pengembangan standar terbuka, dan akses bebas terhadap proses pengembangan teknologi dan kebijakan. Keberhasilan Internet yang belum pernah terjadi sebelumnya terjadi karena modelnya yang terbuka, transparan, dan kolaboratif, dengan fokus pada proses lokal, bottom-up, dan akses global.

<hr>


![height:1in](img/1.1.png)

## 2 Sudut Pandang Internet

- Teknis
  - Routing System (system routing)
  - Naming system (sistem penamaan)
- Arsitektur
  - Standars (standarsiasi)
  - Service Provider (Penyedia layanan)
  - Internet Registries (Internet register)
  - Clearing Houses (Rumah kliring)
<hr>

### IP Addressing & Routing System
Perutean internet adalah proses pengalihan lalu lintas dari berbagai jaringan yang melibatkan pengambilan paket data dari satu titik ke titik tujuan melalui serangkaian perangkat jaringan dan rute yang optimal.

#### a. Routing
<div align="center">
    <img src="img/3.1.png" alt="Routing" width="50%" height="auto"><br>
    <em style="font-size:10px">Gambar 3. a) Routing</em>
</div><br>

<span style="font-size:14px">
Adanya alamat yang mengarah ke situs web diikuti dengan data yang akan ditransfer. Kebijakan merupakan kunci untuk memahami tingkat <em>AS (Overlay Network)</em>. <strong>BGP (Border Gateway Protocol)</strong> mengatur kebijakan yang terdistribusi dengan jenis penyedia untuk memaksimalkan pendapatan dan memininalkan biaya.
</span>

#### b. Peering Connections
<div align="center">
    <img src="img/3.2.png" alt="Peering Connections" width="50%" height="auto"><br>
    <em style="font-size:10px">b) Peering Connections</em>
</div><br>

<span style="font-size:14px">
Untuk memahami kebijakan ini membutuhkan pemangaman mengenai peering models yang mencakup provider atau customer, transit dan settlement free.
</span>

#### c. Edge Provider Routing Policy
<div align="center">
    <img src="img/3.3.png" alt="Edge Provider Routing Policy" width="50%" height="auto"><br>
    <em style="font-size:10px">c) Edge Provider Routing Policy</em>
</div><br>

<span style="font-size:14px">
Jadilah jalur yang dipilih oleh pelanggan yang terhubung. Pilih jalur lalu lintas yang paling pendek dengan waktu sesingkat mungkin, ini dikenal sebagai <em>hot potato routing</em>.
</span>

#### d. Transit Provider Routing Policy
<div align="center">
    <img src="img/3.4.png" alt="Transit Provider Routing Policy" width="60%" height="auto"><br>
    <em style="font-size:10px"> d) Transit Provider Routing Policy</em>
</div><br>

<span style="font-size:14px">
Meningkatkan peering untuk mempersingkat jalur AS dan membawa sebanyak mungkin lalu lintas dengan jarak sesingkat mungkin, ini dikenal sebagai <em>hot potato routing</em>.
</span>

#### e. Content Provider Routing Policy

<span style="font-size:14px">
Mengirimkan konten secepat mungkin dengan menyebarkan peer sebanyak mungkin menggunakan distribusi konten ke setiap sudut jaringan dan mengangkut lalu lintas melalui link internal untuk kontrol pengalaman pengguna yang optimal. Hal ini dikenal sebagai <em>cold potato routing</em>.
</span>

---
<hr>


## Naming System

<div align="center">
    <img src="img/4.1.png" alt="Naming System" width="100%" height="auto"><br>
    <em style="font-size:10px">Gambar 4. Naming System</em>
</div><br>

<span style="font-size:14px">
Gambar diatas menunjukkan cara kerja DNS dalam jaringan. ICANN akan mengkoordinasikan system penamaan internet dan Registries akan mengelola <strong>Top Level Domain (TLD)</strong> seperti <em>.com, .org</em> dan <em>.id</em>. Pada bagian Registries menyediakan layanan DNS kepada registrar yang menjual nama domain kepada pengguna. Kemudian DNS yang akan menerjemahkan nama domain ke alamat IP, ini dikenal sebagai <em>Name to location mapping</em>.
</span>

---

## Domain Name System (DNS)

<div align="center">
    <img src="img/5.png" alt="Domain Name System (DNS)" width="60%" height="auto"><br>
    <em style="font-size:10px">Gambar 5. Domain Name System (DNS)</em>
</div><br>

#### a. DNS Hierarchy Tree

<div align="center">
    <img src="img/5.1.png" alt="Domain Name System (DNS)" width="60%" height="auto"><br>
    <em style="font-size:10px">Gambar 5. a) DNS Hierarchy Tree</em>
</div><br>

<span style="font-size:14px">
DNS Hierarchy Tree adalah struktur yang mencakup semua domain di Internet dalam lima level. Dimulai dari Root Level Domain sebagai level teratas yaitu TLD. Kemudian, ada <strong>Second Level Domains (SLD)</strong>, serta Subdomains. Level terakhir adalah Hosts, yang merupakan segmen paling spesifik seperti example.com. Dengan struktur ini, pengguna dapat mengakses situs web menggunakan nama domain tanpa perlu mengingat alamat IP yang rumit.
</span>

#### b.	DNS Components

<div align="center">
    <img src="img/5.2.png" alt="DNS Components" width="60%" height="auto"><br>
    <em style="font-size:10px">b) DNS Components</em>
</div><br>

<span style="font-size:14px">
DNS memudahkan konversi antara nama domain dan alamat IP. Ini terdiri dari beberapa komponen penting, yaitu Namespace (daftar lengkap domain), Nameserver (server penyimpan informasi domain), Resolver (program yang mengirim permintaan DNS) dan Client (komputer yang mengirim permintaan DNS ke resolver).
</span>

#### c.	Domains

<div align="center">
    <img src="img/5.3.png" alt="Domains" width="60%" height="auto"><br>
    <em style="font-size:10px">c) Domains</em>
</div><br>

<span style="font-size:14px">
Server root sebagai pusat pengelolaan semua domain di internet, di bawahnya terdapat contoh domain tingkat atas seperti .id dan .com, serta domain tingkat kedua seperti .co.id dan .ac.id. Contoh domain juga mencakup subdomain seperti www.pens.ac.id untuk web pendidikan, www.detik.com dan www.kompas.com untuk web berita. Bagian bawah gambar menekankan penggunaan domain untuk situs web dan subdomain untuk layanan email.
</span>

#### d.	Name Server

<div align="center">
    <img src="img/5.4.png" alt="Name Server" width="50%" height="auto"><br>
    <em style="font-size:10px">d) Name Server</em>
</div><br>

<span style="font-size:14px">
Nameserver merupakan bagian penting dalam sistem DNS yang menangani pertanyaan-pertanyaan terkait DNS. Jenis-jenisnya meliputi authoritative servers, terdiri dari Primary dan Secondary, serta recursive servers yang dapat berperan sebagai caching forwarders. Fungsi-fungsi ini sering kali saling terintegrasi dalam satu name server.
</span>

#### e.	Authoritative Nameserver

<div align="center">
    <img src="img/5.5.png" alt="Authoritative Nameserver" width="60%" height="auto"><br>
    <em style="font-size:10px">e) Authoritative Nameserver</em>
</div><br>

<span style="font-size:14px">
Nameserver yang diotorisasi untuk memberikan jawaban untuk suatu domain (bisa lebih dari satu). Berdasarkan metode manajemen terbagi menjadi Primary dan Secondary. Primary nameserver menerima semua perubahan pada zona dilakukan, sementara secondary nameserver mengambil file zona dari primary secara berkala.
</span>

#### f.	Recursive Nameserver

<div align="center">
    <img src="img/5.6.png" alt="Recursive Nameserver" width="60%" height="auto"><br>
    <em style="font-size:10px">f) Recursive Nameserver</em>
</div><br>

<span style="font-size:14px">
Recursive nameserver berfungsi untuk mencari authoritative nameserver dan mendapatkan jawaban, serta berfungsi sebagai caching servers yang memprioritaskan cache lokal untuk mengurangi latensi dan lalu lintas ke link eksternal. Proses ini bersifat iteratif, dimulai dari root.
</span>

#### g.	Root Servers

<span style="font-size:14px">
Puncak hierarki DNS terdiri dari 13 server root nama yang dioperasikan di seluruh dunia, yang ditandai dengan:

    [a-m].root-servers.net. 

Ada lebih dari 13 server fisik yang mewakili root name servers, dimana setiap root server memiliki instansi yang dideploy melalui anycast.
</span>

#### h.	Root Server Deployment at APNIC

<span style="font-size:14px">
Pada tahun 2002, APNIC mendirikan situs-situs server root baru di wilayah AP untuk memperkuat DNS dengan mendeploy sumber daya tambahan yang menangani pertumbuhan lalu lintas internet yang meningkat.
</span>

#### i.	Resource Records

<div align="center">
    <img src="img/5.7.png" alt="Resource Records" width="60%" height="auto"><br>
    <em style="font-size:10px">i) Resource Records</em>
</div><br>

<span style="font-size:14px">
File zona DNS adalah file yang memuat informasi mengenai konten suatu situs web. Contohnya, untuk subdomain <em>training.apnic.net</em>, TTL diatur pada 86400 detik, artinya data akan disimpan dalam cache DNS selama periode tersebut sebelum perlu diperbarui. Kelas DNS diatur sebagai IN yang berarti ini adalah kelas DNS internet. Tipe record adalah A, menandakan bahwa data tersebut adalah alamat IPv4. <strong>RDATA (Resource Data)</strong> berisi alamat IP terkait dengan subdomain tersebut, yakni 192.168.1.100.
</span>

#### j.	Common Resource Record Types

<div align="center">
    <img src="img/5.8.png" alt="Common Resource Record Types" width="60%" height="auto"><br>
    <em style="font-size:10px">j) Common Resource Record Types</em>
</div>

#### k.	Example: RRs in a Zone File

<div align="center">
    <img src="img/5.9.png" alt="Example: RRs in a Zone File" width="60%" height="auto"><br>
    <em style="font-size:10px">k) Example: RRs in a Zone File</em>
</div><br>

<span style="font-size:14px">
Zone file merupakan sebuah file teks yang memetakan nama domain ke alamat IP. RR dalam file zona memiliki beberapa bidang yang berbeda.

- SOA (Start of Authority) untuk domain apnic.net. yang mengarah ke server nama utama ns.apnic.net. dan administrator admin.apnic.net.
- NS (Name Server) yang menunjuk ke server nama ns.apnic.net. dan ns.ripe.net. untuk menyelesaikan nama domain apnic.net.
- A (Address) yang memetakan nama domain www.apnic.net. ke alamat IP 192.168.0.2.

</span>

#### l.	DNS Data Flow

<div align="center">
    <img src="img/5.10.png" alt="DNS Data Flow" width="60%" height="auto"><br>
    <em style="font-size:10px">l) DNS Data Flow</em>
</div><br>

<span style="font-size:14px">
Administrator zona bertanggung jawab untuk membuat atau memperbarui file zona di server master. Setiap perubahan yang terjadi pada file zona disinkronkan ke server slave. Ketika pengguna memasukkan nama domain ke browser web, resolver mereka mengirimkan permintaan ke server DNS. Server DNS kemudian memeriksa file zonanya untuk menemukan catatan sumber daya yang sesuai dengan nama domain yang diminta. Setelah menemukan RR yang cocok, server DNS mengembalikan alamat IP yang terkait dengan nama domain tersebut ke resolver. Selanjutnya, resolver menggunakan alamat IP untuk terhubung ke server web yang sesuai.
</span>

#### m.	Delegating a Zone

<div align="center">
    <img src="img/5.11.png" alt="Delegating a Zone" width="60%" height="auto"><br>
    <em style="font-size:10px">m) Delegating a Zone</em>
</div><br>

<span style="font-size:14px">
Delegasi zona dilakukan dengan menambahkan catatan NS untuk menunjukkan nameserver yang bertanggung jawab atas subdomain tertentu. Dalam contoh ini, zona apnic.net mendelegerikan subdomain academy.apnic.net ke dua nameserver, yaitu ns1.academy.apnic.net dan ns2.academy.apnic.net. Untuk mengakses subdomain tersebut, klien harus mengarahkan permintaannya ke salah satu nameserver tersebut. Untuk mencapai nameserver ns1 dan ns2, diperlukan penambahan Glue Record.
</span>

#### n.	Glue Record

<div align="center">
    <img src="img/5.12.png" alt="Glue Record" width="60%" height="auto"><br>
    <em style="font-size:10px">n) Glue Record</em>
</div><br>

<span style="font-size:14px">
Glue record adalah data non-authoritative yang merupakan sebuah catatan A yang memetakan alamat dari nameserver sub-domain.
</span>

---

## Standards Bodies

<div align="center">
    <img src="img/6.png" alt="Standards Bodies" width="60%" height="auto"><br>
    <em style="font-size:10px">Gambar 6. Standards Organizations</em>
</div><br>

<span style="font-size:14px">

- IETF
Semua protokol transportasi dan routing layer 3, termasuk IP, TCP, UDP, HTTP, DNS, protokol routing, telnet, rsync, IPsec, dan protokol manajemen jaringan. IETF memiliki beberapa area fokus yang berbeda. Area Umum (gen), Keamanan (sec), Aplikasi dan Real Time (art), Operasi dan Manajemen Internet (ops), Layanan Transportasi (tsv), Routing (rtg), dan Internet (int). Setiap area bertanggung jawab atas aspek tertentu dalam pengembangan standar IETF.<br><br>

- IEEE
Semua protokol transportasi dan kontrol plane di layer 1 dan layer 2, termasuk Ethernet, spanning tree, dan jaringan nirkabel.<br><br>

- W3C
Bahasa markup (bahasa yang menjelaskan cara menampilkan atau merender konten), termasuk HTML dan XML.<br><br>

- ITU
Standar internasional apa pun, termasuk penomoran, skema enkripsi, dan protokol routing (seperti IS-IS).
</span>

---

## Service Providers

#### a. Content Provider Overview

<span style="font-size:14px">
Penyedia konten terbagi menjadi dua: yang menciptakan dan mendistribusikan media, serta yang menghubungkan pembeli dan penjual dalam e-commerce. Tujuan utama mereka adalah menarik perhatian pengguna, terutama untuk keperluan periklanan.
</span>

#### b. Access Provider Overview

<span style="font-size:14px">
Memberikan koneksi internet kepada pengguna, bisnis, dan organisasi serta terlibat dalam pembuatan dan distribusi konten.
</span>

#### c. Transit Provider overview

<div align="center">
    <img src="img/7.1.png" alt="Transit Provider overview" width="60%" height="auto"><br>
    <em style="font-size:10px">Gambar 7. a) Transit Provider overview</em>
</div><br>

<span style="font-size:14px">
Menghubungkan penyedia konten dengan penyedia layanan akses untuk memastikan akses yang lancar dan efisien bagi pengguna. Ini memungkinkan konten untuk diakses dengan mudah melalui jaringan yang disediakan oleh penyedia akses. Dengan menjembatani keduanya, pengguna dapat dengan cepat mengakses berbagai layanan dan konten online tanpa hambatan.
</span>

#### d. Internet Exchange Point Overview

<div align="center">
    <img src="img/7.2.png" alt="Internet Exchange Point Overview" width="60%" height="auto"><br>
    <em style="font-size:10px">b) Internet Exchange Point Overview</em>
</div><br>

<span style="font-size:14px">
Internet Exchange Points (IXPs) adalah tempat pertukaran data lokal yang memungkinkan penyedia akses dan penyedia konten untuk terhubung secara langsung. IXPs bisa bersifat komersial atau non-profit dan digunakan oleh penyedia layanan dalam suatu wilayah. Dengan menggunakan IXPs, penyedia layanan dapat menghindari penggunaan penyedia transit di luar wilayah, sehingga mengurangi latensi dalam wilayah tersebut. Selain itu, IXPs menggantikan biaya penyelesaian berbasis lalu lintas dengan biaya keanggotaan tetap.
</span>

---

## Registries

#### a. Naming Authorities

<span style="font-size:14px">
ICANN dan IANA mengoordinasikan penugasan angka dan nama yang mendukung fungsi Internet serta menetapkan aturan bagi organisasi lain untuk memperoleh sumber daya tersebut.
</span>

#### b. Regional Registry Overview

<div align="center">
    <img src="img/8.png" alt="Regional Registry Overview" width="60%" height="auto"><br>
    <em style="font-size:10px">Gambar 8. Regional Registry Overview</em>
</div><br>

<span style="font-size:14px">
Regional Internet Registries (RIRs) mengelola penugasan blok alamat IP untuk wilayah tertentu, serta terlibat dalam penelitian, standarisasi, dan menyediakan layanan penting seperti whois. IANA memberikan blok alamat IP kepada setiap RIR berdasarkan kebutuhan, yang kemudian diteruskan ke anggotanya untuk penggunaan dalam tabel routing global, entri DNS atau jaringan internal.
</span>

#### c. Top Level Registries

<span style="font-size:14px">
Domain Name Registries mengelola TLDs atas izin ICANN. Mereka menjual nama domain kepada registri tingkat kedua, termasuk ccTLDs yang merepresentasikan negara atau wilayah geografis.
</span>

#### d. Second Tier Registries

<span style="font-size:14px">
Domain resellers membeli domain dari registrar TLD dengan harga tetap dan kemudian menjualnya berdasarkan popularitas, bundel dengan layanan lain, dan sebagainya.
</span>

---

## Other Entities

#### a. Clearing House

<div align="center">
    <img src="img/18.png" alt="Clearing House" width="100%" height="auto"><br>
    <em style="font-size:10px">Clearing House</em>
</div><br>

<span style="font-size:14px">
NOGs dan asosiasi lainnya bertindak sebagai pusat pengelolaan operasional, sedangkan IRRs bertindak sebagai pusat pengelolaan kebijakan dan status jaringan. Para penyedia konten menciptakan konten dan mendistribusikannya melalui jaringan distribusi konten.
</span>

#### b. Internet Route Registries

<span style="font-size:14px">
Internet Routing Registries (IRRs) adalah basis data yang dikembangkan secara kolaboratif dan sering dijalankan oleh relawan, seperti registrar dan lembaga riset. Beberapa organisasi seperti RIPE, APNIC, ARIN, EasyNet, dan Level3 menyediakan salinan IRR. Data disimpan dalam format standar yang disebut Routing Policy Specification Language (RPSL), yang digunakan oleh penyedia layanan untuk membangun filter rute dan menentukan kebijakan jaringan.
</span>

#### c. Network Operators Groups

<div align="center">
    <img src="img/19.jpg" alt="Network Operators Groups" width="30%" height="auto"><br>
    <em style="font-size:10px">Clearing House</em>
</div><br>

<span style="font-size:14px">
Network Operator's Groups (NOGs) adalah pusat informasi untuk operasi jaringan. Biasanya, mereka adalah organisasi relawan yang bekerja dengan registrar regional, lembaga riset, vendor, dan organisasi regional lainnya.
</span>