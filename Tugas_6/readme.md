**Pengertian Web Server & Web Client**   
   Web client dan Web server berkomunikasi menggunakan protokol HTTP (HyperText Transfer Protocol). Web client adalah komputer yang tergabung dalam jaringan atauinternet yang meminta informasi. Untuk dapat mengakses web server, web client menggunakan aplikasi yang disebut Web browser. Web server adalah komputer yang tergabung dalam jaringan atau internet yang memberikan informasi.

**Fungsi Web Server & Web Client**  
- Fungsi Client :
Client Fungsi utama Client adalah menghasilkan permintaan untuk berbagai layanan yang bersumber dari server. Client juga dapat dinonaktifkan sewaktu-waktu. Contoh klien adalah smartphone, desktop, laptop, dan lainnya.
- Fungsi Web Server :
    - Mentransfer data yang diminta user
Biasanya, sebuah laman web terdiri dari berbagai macam informasi dalam berbagai bentuk, seperti teks, video, gambar, audio, atau dokumen. Berkas-berkas inilah yang nantinya akan dikirimkan ke browser-mu sesuai permintaan. Pada praktiknya langsung, web server akan merespon permintaan yang kamu tulis di address bar dan informasi yang kamu minta tadi akan ditampilkan ke browser-mu. Jika permintaanmu tidak bisa dicari, maka web server akan melakukan pengiriman balik berupa penolakan dengan cara memberikan informasi yang biasa dikenal dengan kode ‘404’, artinya kata kunci yang kamu cari tidak bisa ditemukan.
    - Memeriksa keamanan dari permintaan HTTP
Selain itu, web server berfungsi untuk memeriksa sistem keamanan dari request HTTP
yang diminta oleh klien atau web browser. Web server menggunakan HTTP/HTTPS
sebagai perantara untuk menghubungkan website dengan web server. Proses transfer
data yang dilakukan bersifat privat dan tidak bisa diakses sembarangan oleh publik.


**Cara kerja Web Server**

   ![alt text](img/carakerja.png) <br>

1. Client melakukan permintaan untuk mengakses sebuah domain Uniform Resource Locator (URL) yang diketikkan pada address bar di sebuah browser
2. Permintaan tersebut dikirim ke server penyedia DNS.
3. Bila halaman web tersebut menggunakan database programming, maka akan dihubungkan dengan database server
4. Apabila domain pada URL tersebut ada di web server, maka web server akan segera melakukan respon, dengan menampilkan web yang diinginkan.
5. Apabila domain pada URL tersebut tidak ada, maka akan muncul informasi "Page Not Found" artinya halaman tidak ditemukan.
6. Pengiriman permintaan web dari client tersebut akan didelegasikan melalui DNS server.
7. Demikian seterusnya, karena setiap perangkat terhubung ke internet dan memiliki spesifikasi yang baik, juga dengan koneksi internet yang cukup, maka proses permintaan web tidak akan berlangsung lama.


**Cara kerja Web Client**

   ![alt text](img/carakerja2.png) <br>

1. Client dapat membangun sebuah halaman web berdasarkan database yang dimiliki, dengan menggunakan perangkat keras (hardware) dan software. Sehingga, menghasilkan tampilan atau UI tertentu. 
2. Server dapat mempengaruhi UI. Server web menerima permintaan dan menyimpan UI web tersebut berupa dokumen HTML. 
3. Client yang meminta akses informasi, dalam hal ini adalah pengguna, maka server akan mengirimkan dokumen HTML tersebut. Hasilnya informasi tampil di browser dan kamu dapat membacanya dengan tampilan UI yang menarik dan mudah dimengerti. 
4. Ketika client (pengguna) sudah mendapatkan informasinya, maka client akan memeriksa kode program atau sintaks. Proses ini menghasilkan database yang diperlukan. Proses ini menggunakan bahasa pemrograman SQL atau sejenisnya. 
5. Proses tersebut diteruskan ke server, sambil menunggu server mendapat respons dari pengguna akhir. Ketika pengguna merespons, permintaan database dibuat untuk client dan hasilnya tayang di layar kamu. 
