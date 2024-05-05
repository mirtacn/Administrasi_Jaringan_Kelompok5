<div align="center">
  <h2 style="text-align: center;font-weight: bold">Praktikum 5<br>Instalasi dan Konfigurasi Web Server, Database Server, dan Mail Server</h2>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h4 style="text-align: center;">Disusun Oleh :</h4>
  <p style="text-align: center;">
    <strong>Mirta Chadhirotin Nachlah (3122500009)</strong>
  </p>
<h4 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2023/2024</h4>
  <hr>
</div>

# Daftar Isi

| Nomor | File                                                                        |
| ----- | --------------------------------------------------------------------------- |
| 1     | [Konfigurasi NTP Server](#NTP-Server)                                       |
| 2     | [Konfigurasi Web Server](#Apache-2-dan-PHP-FM)                              |
| 3     | [Konfigurasi Database Server](#MariaDB-&-PhpMyAdmin)                        |
| 4     | [Konfigurasi mail server](#Email-System)                                    |
| 5     | [Final Check All Services](#Final-Check-All-Services)                       |
| 6     | [Test Email With Email Client - Thunderbird](#Thunderbird-Email-GUI-Client) |
| 7     | [Konfigurasi roundcube](#Roundcube-Webmail)                                 |
| 8     | [(Tambahan) Praktikum Mail Server Antar Kelompok](#Melanjutkan-setup-web-email-server) |

---

# NTP Server

1.  Lakukan instalasi paket layanan sinkronisasi waktu → `sudo apt install systemd-timesyncd`
    <img src="img/1.png" width="42%" height="auto"><br>

2.  Melakukan konfigurasi timezone ke Asia/Jakarta → `sudo timedatectl set-timezone Asia/Jakarta`
    <img src="img/2.png" width="40%" height="auto"><br>

3.  Melakukan konfigurasi Real Time Clock (RTC) untuk merefer ke UTC (Coordinated Universal Time) → `sudo timedatectl set-local-rtc false`
    <img src="img/3.png" width="40%" height="auto"><br>

4.  Mengaktifkan NTP Client untuk sinkronisasi waktu → `sudo timedatectl set-ntp true`
    <img src="img/4.png" width="50%" height="auto"><br>

5.  Menyunting file timesyncd.conf untuk mengarah ke NTP server terdekat untuk mendapatkan waktu delay terpendek. Biasanya setiap organisasi atau negara mempunyai NTP Server sendiri → `sudo nano /etc/systemd/timesyncd.conf`
    <img src="img/5.png" width="51%" height="auto"><br>

6.  Restart layanan sinkronisasi waktu dan pastikan layanan berjalan dengan benar

        `sudo systemctl restart systemd-timesyncd`

    <img src="img/6.png" width="40%" height="auto"><br>
Mengecek status layanan sinkronisasi waktu → `sudo systemctl status systemd-timesyncd`
    <img src="img/7.png" width="42%" height="auto"><br>
Dapat dilihat status active(running)

7.  Lakukan pengecekan kesesuaian tanggal system dengan perintah → `timedatectl`
    <img src="img/8.png" width="50%" height="auto"><br>
Menampilkan status sinkronisasi waktu pada sistem dengan server NTP (Network Time Protocol) → `sudo timedatectl timesync-status`
 <img src="img/9.png" width="40%" height="auto"><br>

Bisa dilihat sudah tersambung ke NTP 0.id.pool.ntp.org, dan memiliki delay waktu yang terbilang cukup kecil yaitu +- 30ms

# Apache 2 dan PHP-FM

## Install Apache2

1.  Install Apache2 → `sudo apt -y install apache2`
    <img src="img/10.png" width="63%" height="auto"><br>

2.  Melakukan konfigurasi Apache2

- `sudo nano /etc/apache2/conf-enabled/security.conf`  
    <img src="img/11.png" width="40%" height="auto"><br>

  Mengganti line 12 --> `ServerTokens Prod` --> berarti Apache hanya akan menampilkan informasi identifikasi server yang minimal dalam header responsnya.

- `sudo nano /etc/apache2/mods-enabled/dir.conf`
    <img src="img/hi.png" width="70%" height="auto"><br>

  Menambahkan nama file yang hanya bisa diakses dengan nama direktori, yaitu index.html, index.htm, dan index.php

- `sudo nano /etc/apache2/apache2.conf`
    <img src="img/12.png" width="69%" height="auto"><br>

  Line 70 --> Menambahkan specify server name

- `sudo nano /etc/apache2/sites-enabled/000-default.conf`
    <img src="img/13.png" width="60%" height="auto"><br>

  Mengganti line 11 --> Mengganti webmaster's email

- `systemctl reload apache2`
    <img src="img/15.jpeg" width="50%" height="auto"><br>

  Melakukan reload layanan apache

3.  Melakukan test ke web browser
    <img src="img/load.png" width="78%" height="auto"><br>

## Install PHP 8.2

1.  Melakukan install PHP versi 8.2 beserta modul mbstring dan paket pear --> `sudo apt -y install php8.2 php8.2-mbstring php-pear`
    <img src="img/14.png" width="78%" height="auto"><br>

2.  Mengecek php version → `php -v`
    <img src="img/load.png" width="78%" height="auto"><br>
    Karena sudah muncul version dari php, berarti php telah berhasil terinstall

3.  Melakukan test terhadap php

    - `nano php_test.php`
    <img src="img/16.png" width="78%" height="auto"><br>

      Membuat file php_test.php, yang akan mencetak ouytput dari `php -i` ketika dijalankan

    - Jalankan `php php_test.php | head`
    <img src="img/17.png" width="78%" height="auto"><br>
        Akan menampilkan output dari `php -i` yaitu menampilkan informasi terkait konfigurasi PHP

4.  Melakukan Install PHP-FM → `sudo apt -y install php-fpm`
    <img src="img/18.png" width="78%" height="auto"><br>

5.  Mengkonfigurasi PHP-FM pada file konfigurasi Apache - `sudo nano /etc/apache2/sites-available/default-ssl.conf`
    <img src="img/19.png" width="78%" height="auto"><br>

    Menambahkan diantara tag < VirtualHost> - < /VirtualHost> yaitu mengatur Apache HTTP Server agar dapat meneruskan permintaan PHP ke PHP-FPM (PHP FastCGI Process Manager)

    - `sudo a2enmod proxy_fcgi setenvif`
    <img src="img/20.png" width="78%" height="auto"><br>
    
      digunakan untuk mengaktifkan modul-modul proxy_fcgi dan setenvif dalam server Apache.

    - `sudo a2enconf php8.2-fpm`
    <img src="img/21.png" width="78%" height="auto"><br>
      digunakan untuk mengaktifkan modul-modul php8.2-fpm

    - `sudo systemctl restart php8.2-fpm apache2`
    <img src="img/23.png" width="78%" height="auto"><br>
      Melakukan restart service php8.2-fpm dan apache2

6.  Melakukan test validasi terhadap PHP-FM dengan membuat file info.php di root document → `sudo nano /var/www/html/info.php`
    <img src="img/22.png" width="78%" height="auto"><br>
    Membuat file info.php yang nanti nya outputnya akan menjalankan command `phpinfo()`

7.  Melakukan test di browser, membuka file info.php di browser
    <img src="img/web.png" width="78%" height="auto"><br>
    Jika berhasil, maka akan menampilkan semua informasi terkait php.

# MariaDB & PhpMyAdmin

## Install MariaDB

1.  Melakukan install mariadb-server --> `sudo apt -y install mariadb-server`
    <img src="img/24.png" width="78%" height="auto"><br>
2.  `sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf`
    <img src="img/25.png" width="78%" height="auto"><br>
    Pada line 95 --> Mengkonfirmasi default charset menggunakan utf8mb4.

3.  `sudo systemctl restart mariadb`
    <img src="img/restt.png" width="78%" height="auto"><br>
    Melakukan restart service mariadb

4.  Inisial Konfigurasi dan testing database MariaDB Server - `sudo mysql_secure_installation`
    <img src="img/26.png" width="78%" height="auto"><br>
    Melakukan beberapa tindakan keamanan standar dalam instalisasi MariaDB, Ditahap ini akan di beri beberapa pertanyaan keamanan. Seperti set MariaDB root password, remove anonymous users, dll.

    - Connect to MariaDB → `sudo mysql`
    <img src="img/28.png" width="78%" height="auto"><br>
    - Menampilkan hak akses yang dimiliki oleh user root → `show grants for root@localhost;`
    <img src="img/29.png" width="78%" height="auto"><br>

    - Menampilkan semua daftar user → `select user,host,password from mysql.user;`
    <img src="img/30.png" width="85%" height="auto"><br>

    - show database list → `show databases;`
    <img src="img/31.png" width="78%" height="auto"><br>

    - create test database → `create database test_database;`
    <img src="img/33.png" width="78%" height="auto"><br>

    - create test table on test database → `create table test_database.test_table (id int, name varchar(50), address varchar(50), primary key (id));`
    <img src="img/32.png" width="78%" height="auto"><br>

    - insert data to test table → `insert into test_database.test_table(id, name, address) values("001", "Debian", "Hiroshima");`
    <img src="img/34.png" width="78%" height="auto"><br>

    - show test table → `select * from test_database.test_table;`
    <img src="img/35.png" width="78%" height="auto"><br>

    - delete test database → `drop database test_database;`
    <img src="img/36.png" width="78%" height="auto"><br>

## Install PhpMyAdmin

1.  Melakukan install phpmyadmin --> `sudo apt install phpmyadmin`
2.  Pilih Apache2 sebagai web server
    <img src="img/ei.png" width="78%" height="auto"><br>

3.  Pilih **yes** agar konfigurator melakukan langkah-langkah yang diperlukan untuk membuat database dan pengguna khusus untuk phpMyAdmin agar dapat berfungsi dengan baik.
    <img src="img/27.png" width="85%" height="auto"><br>

4.  Masukkan password phpmyadmin
    <img src="img/nxt.png" width="78%" height="auto"><br>
    <img src="img/37.png" width="78%" height="auto"><br>

5.  Menambahkan konfigurasi phpmyadmin di apache2 → `sudo nano /etc/apache2/apache2.conf`
    <img src="img/38.png" width="78%" height="auto"><br>
    Mendaftarkan file `/etc/phpmyadmin/apache.conf`

6.  Coba membuka phpmyadmin di web browser    
    <img src="img/40.png" width="78%" height="auto"><br>
    <img src="img/41.png" width="78%" height="auto"><br>

7.  Menambahkan privillege ke user phpmyadmin - Login ke mariadb → `sudo mariadb -u root -p` - Lalu berikan hak akses penuh kepada user phpmyadmin → `GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION; FLUSH PRIVILEGES;`
    <img src="img/42.png" width="78%" height="auto"><br>
    <img src="img/hm.png" width="78%" height="auto"><br>

    Bisa dilihat sekarang user phpmyadmin, memiliki hak akses penuh seperti create database, dll.

# Email System

## POSTFIX : SMTP Server (TCP 25)

1.  Melakukan install postfix sasl2-bin --> `sudo apt -y install postfix sasl2-bin`
2.  Pilih no configuration, karena kita akan melakukan konfigurasi secara manual
    <img src="img/43.png" width="78%" height="auto"><br>

3.  Mencopy file /usr/share/postfix/main.cf.dist ke /etc/postfix/main.cf --> `sudo cp /usr/share/postfix/main.cf.dist /etc/postfix/main.cf`
    <img src="img/44.png" width="78%" height="auto"><br>

4.  `sudo nano /etc/postfix/main.cf` - Uncoment line 82
    <img src="img/45.png" width="78%" height="auto"><br>
    - Uncoment line 98 dan isi dengan email hostname kelompok5
    <img src="img/47.png" width="78%" height="auto"><br>

    - Uncoment line 106 dan isi dengan hostname kelompok5
    <img src="img/48.png" width="78%" height="auto"><br>

    - Uncoment line 127
    <img src="img/49.png" width="78%" height="auto"><br>

    - Uncoment line 141
    <img src="img/50.png" width="78%" height="auto"><br>

    - Uncoment line 189
    <img src="img/46.png" width="78%" height="auto"><br>

    - Uncoment line 232
    <img src="img/lost.png" width="78%" height="auto"><br>

    - Uncoment line 277
    <img src="img/51.png" width="78%" height="auto"><br>

    - Uncoment line 294 dan tambahkan local network
    <img src="img/lk.png" width="78%" height="auto"><br>

    - Uncoment line 416
    <img src="img/52.png" width="78%" height="auto"><br>

    - Uncoment line 427
    <img src="img/53.png" width="78%" height="auto"><br>

    - Uncoment line 449
    <img src="img/54.png" width="78%" height="auto"><br>

    - Comment line 558 dan tambahkan di line 589 konfigurais smtpd_banner
    <img src="img/55.png" width="78%" height="auto"><br>

    - Tambahkan di line 659 sendmail_path
    <img src="img/krg.png" width="78%" height="auto"><br>

    - Tambahkan di line 664 newaliases_path
    <img src="img/56.png" width="78%" height="auto"><br>

    - Tambahkan di line 669 mailq_path
    <img src="img/57.png" width="78%" height="auto"><br>

    - Tambahkan di line 675 setgid_group
    <img src="img/58.png" width="78%" height="auto"><br>

    - Comment line 679    
    <img src="img/59.png" width="78%" height="auto"><br>

    - Comment line 683
    <img src="img/60.png" width="78%" height="auto"><br>

    - Comment line 688
    <img src="img/61.png" width="78%" height="auto"><br>

    - Comment line 692
    <img src="img/62.png" width="78%" height="auto"><br>

    - Tambahkan internet protocol di line 692
    <img src="img/63.png" width="78%" height="auto"><br>

    - Menambahkan config di line terakhir. Yaitu mematikan SMTP VRFY command, require HELO command to sender hosts, Mengatur limit an email size, dan mengatur SMTP-Auth settings
    <img src="img/64.png" width="78%" height="auto"><br>

5.  Meng-update database alias untuk sistem postfix --> `sudo newaliases`
    <img src="img/65.png" width="78%" height="auto"><br>

6.  Melakukan restart layanan postfix --> `systemctl restart postfix`
    <img src="img/66.png" width="78%" height="auto"><br>

7.  Menambahkan konfigurasi anti spam

    - `sudo nano /etc/postfix/main.cf`
    <img src="img/67.png" width="78%" height="auto"><br>

    - Melakukan restart layanan postfix --> `sudo systemctl restart postfix`
    <img src="img/68.png" width="78%" height="auto"><br>

## Install **DOVECOT : IMAP4 (TCP 143) and POP3 (TCP110)**

1.  Melakukan install dovecot-core, dovecot-pop3d, dovecot-imapd --> `sudo apt -y install dovecot-core dovecot-pop3d dovecot-imapd`
    <img src="img/s.png" width="78%" height="auto"><br>

2.  `sudo nano /etc/dovecot/dovecot.conf`
    <img src="img/d.png" width="78%" height="auto"><br>
    Uncoment line 30 agar Dovecot mendengarkan koneksi pada semua antarmuka jaringan yang tersedia.

3.  `sudo nano /etc/dovecot/conf.d/10-auth.conf`
    <img src="img/69.png" width="78%" height="auto"><br>

    Uncoment line 10 dan izinkan plain text auth - Tambahkan auth_mechanisms di line 100
    <img src="img/70.png" width="78%" height="auto"><br>

4.  `sudo nano /etc/dovecot/conf.d/10-mail.conf`
    <img src="img/71.png" width="78%" height="auto"><br>
    Ubah mail location di line30 menjadi Maildir

5.  `sudo nano /etc/dovecot/conf.d/10-master.conf`
    <img src="img/72.png" width="78%" height="auto"><br>
    Tambahkan Postfix smtp-auth di line 107 - 109

6.  Restart layanan dovecot --> `sudo systemctl restart dovecot`
    <img src="img/73.png" width="78%" height="auto"><br>

# Final Check All Services

1.  `netstat -a| grep LISTEN`
    <img src="img/74.png" width="78%" height="auto"><br>
    Akan terlihat hasilnya dengan status Server (LISTEN) : MariaDB(MySQL), IMAP, POP3, DNS(domain - http), IMAPS, POP3S, SSH, Postfix (SMTP)

2.  Melakukan Cek terhadap Layanan Posfix `telnet mail.kelompok5.local 25`
    <img src="img/75.png" width="78%" height="auto"><br>
    Memeriksa apakah server mail.kelompok5.local dapat menerima koneksi pada port 25. Lalu menjalankan command `ehlo mail.kelompok5.local` yang digunakan untuk memberikan informasi tentang kemampuan server, seperti fitur-fitur yang didukung atau batasan konfigurasi.

# Thunderbird Email GUI Client

1.  Melakukan install Thunderbird melalui flatpak --> `flatpak install flathub org.mozilla.Thunderbird`
    <img src="img/iyh.png" width="78%" height="auto"><br>

2.  Menginstall thunderbird GUI dari https://flathub.org/apps/org.mozilla.Thunderbird
    <img src="img/thumbnail.png" width="78%" height="auto"><br>

3.  Menambahkan 2 akun email ( yaitu user mirta dan root )
    <img src="img/90.png" width="78%" height="auto"><br>

4.  Mencoba saling send email - User root mencoba send email ke user mirta
    <img src="img/91.png" width="78%" height="auto"><br>

    - User mirta mengek email yang diterima
    <img src="img/92.png" width="78%" height="auto"><br>

**Additional :** Untuk melakukan penambahan akun email anda dapat melalui terminal dengan command yang sama saat melakukan penambahan user. `sudo adduser <namauser>`. Nantinya anda akan disuruh mengisi informasi terkait user tersebut.

# Roundcube Webmail

1.  Membuat database yang nantinya digunakan untuk roundcube
    <img src="img/p.png" width="78%" height="auto"><br>

2.  Melakukan Install dan konfigurasi RoundCube - Melakukan install roundcube -->`sudo apt -y install roundcube roundcube-mysql`
    pilih no karena akan melakukan konfigurasi secara manual
    <img src="img/q.png" width="78%" height="auto"><br>
    <img src="img/r.png" width="78%" height="auto"><br>

3.  Masuk ke directory roundcube --> `cd /usr/share/dbconfig-common/data/roundcube/install`
    <img src="img/kk.png" width="78%" height="auto"><br>

4.  Mengimpor file mysql ke dalam database roundcube dengan menggunakan akun pengguna (-u roundcube) dan database (-D roundcube) yang sesuai. --> `sudo mysql -u roundcube -D roundcube -p < mysql`
    dan masukkan password mariaDB user roundcube (password)  
    <img src="img/kd.png" width="78%" height="auto"><br>

5.  Melakukan set database informasi --> `sudo nano /etc/roundcube/debian-db.php`
    <img src="img/-u.png" width="78%" height="auto"><br>

6.  `sudo nano /etc/roundcube/config.inc.php`
    <img src="img/kunbir.png" width="78%" height="auto"><br>
    Melakukan konfigurasi imap_host, smtp_host, smtp user dan password

7.  `sudo nano /etc/apache2/conf-enabled/roundcube.conf`
    <img src="img/hk.png" width="78%" height="auto"><br>
    Mengatur agar ketika membuka path /roundcube di domain kita, akan di arahkan ke dirctory /var/lib/roundcube.

8.  Melakukan restart service apache2 --> `sudo systemctl restart apache2`
9.  Mencoba membuka roundcube di web browser (domain/roundcube)
    <img src="img/home.png" width="78%" height="auto"><br>

10. Mencoba send email
    User 1 mengirim email ke user mirta
    <img src="img/cekmil1.png" width="78%" height="auto"><br>
    
    Pesan berhasil terkirim :
    <img src="img/centang.png" width="30%" height="auto"><br>

    User mirta mengecek email yang diterima :
    <img src="img/cekmil2.png" width="78%" height="auto"><br>


# Melanjutkan setup web email server
1. Mengubah network NAT menjadi Bridged Adapter dengan name Realtek USB FE Family Controller
   ![alt text](img/pic84.png)
   
2. Mengubah IP menjadi 192.168.5.10 
   ![alt text](img/pic85.png)
   ![alt text](img/pic86.png)

3. Mengubah file nano named.conf.options
   ![alt text](img/pic87.png)
   ![alt text](img/pic88.png)

4. Mengubah file /etc/resolv.conf <br>
    ![alt text](img/pic89.png)

5. Melakukan pengecekkan dengan nslookup <br>
    ![alt text](img/pic90.png)

6. Melakukan setting WinBox
   ![alt text](img/pic91.png)
   
7. Melakukan Testing atau uji coba
   - Melakukan pengepingan pada detik.com
   ![alt text](img/pic92.png)
   - Melakukan pengepingan pada ip kelompok6
   ![alt text](img/pic93.png)

8. Melakukan pengiriman pesan antar kelompok dengan RoundCube
   - Melakukan pengiriman pesan dari arsyita@mail.kelompok5.local ke iqbal@mail.kelompok6.local
    ![alt text](img/pic94.jpg)
   - Melakukan penerimaan pesan dari adam@mail.kelompok8.local ke arsyita@mail.kelompok5.local
    ![alt text](img/pic95.png)


## Melanjutkan Tugas 5 (SMTP, POP3, dan MIME)
### SMTP
![alt text](img/telnetsmtp.jpg)
![alt text](img/telnetsmtp1.jpg)

![alt text](img/client.jpg)
> Pengiriman email dari client (device lainnya)

Simple Mail Transfer Protocol (SMTP) adalah sebuah protokol standar untuk mengirim email di internet. SMTP biasa bekerja ketika mengirim email dari email client ke email server lain atau dari satu email server ke email server lainnya. 
Dari praktek di atas, kami menghubungkan ke IP 192.168.5.10 melalui protokol telnet dengan port 25. Port 25 merupakan port non-enkripsi default SMTP. Dengan perintah tersebut, kami menghubungkan ke server email yang mungkin berjalan di alamat IP tersebut.

- `ehlo mail.kelompok5.local` untuk mengkoneksikan ke server email dibuat.
- `mail from` untuk menentukan alamat email pengirim.
- `rcpt to` untuk menentukan alamat email penerima.

### POP3
![alt text](img/telnetpop3.jpg)
![alt text](img/telnetpop3-3.jpg)
![alt text](img/telnetpop3-4.jpg)
![alt text](img/telnetpop3-5.jpg)
![alt text](img/telnetpop3-6.jpg)

Post Office Protocol version 3 atau POP3 adalah sebuah protokol email standard yang digunakan untuk menerima email dari sebuah server email ke email client yang digunakan. Dengan POP3, kita dapat mendownload pesan-pesan yang ada pada server email ke komputer atau device dan bisa membacanya bahkan ketika komputer offline atau tidak terkoneksi dengan internet. Jika menggunakan POP3 untuk berhubungan dengan akun email, email-email kita akan didownload ke device lokal dan dihapus dari server email kita. Jadi, jika ingin bisa mengakses email dari beberapa aplikasi yang berbeda, POP3 bukanlah pilihan yang tepat. 
Dari praktek di atas, kami menghubungkan ke IP 192.168.5.10 melalui protokol telnet dengan port 110. Port 110 merupakan port non-enkripsi default POP3. 

- `user arsyita` untuk melakukan login/masuk sebagai arsyita.
- `pass Surabaya24` untuk memasukkan password.
- `list` untuk melihat jumlah daftar pesan email yang diterima.
- `retr 33` untuk melihat dan membuka pesan email dari salah satu email yang diterima sesuai dengan nomor urutannya.

### MIME
![alt text](img/mime3.jpg)

#### Analisa header MIME
- Return-Path digunakan untuk menentukan alamat email yang akan menerima laporan undelivered dari sistem email.
- X-Original-To untuk memberikan informasi tentang alamat tujuan asli dari pesan tersebut sebelum proses pengiriman lanjutan.
- Delivered-To untuk menunjukkan alamat email tujuan di level pengiriman yang paling terakhir.
Received untuk mencatat informasi seperti waktu, alamat IP, dan nama host server yang memproses pesan tersebut.
- MIME-Version untuk melihat versi MIME yang digunakan dalam pesan mail ini
- Date untuk memberikan informasi tanggal dan waktu pesan dikirm
- From berisi alamat mail pengirim pesan
- To berisi alamat mail penerima pesan
- Subject merupakan subject atau topik dari suatu pesan
- User-Agent untuk memberikan informasi tentang klien email atau perangkat lunak yang digunakan oleh pengirim kepada penerima.
- Message-ID seperti nomor id (identitas) dari pesan, dan biasanya unik.
- X-Sender untuk memberikan informasi tambahan tentang identitas pengirim pesan kepada penerima.
- Content-Type berisi tipe konten yang terdapat dalam pesan tersebut.

Fungsi dari Content-Type adalah:
1. Menentukan Jenis Konten: menyatakan jenis konten yang terdapat dalam bagian pesan tertentu, seperti teks biasa, HTML, gambar, lampiran, audio, atau video. Sehingga, klien email mengetahui cara menangani dan menampilkan konten pesan dengan benar.
2. Menentukan Pengaturan Karakter: seperti UTF-8 atau ISO-8859-1. Ini penting untuk memastikan bahwa karakter dalam pesan ditampilkan dengan benar, terutama jika pesan mengandung teks dalam bahasa dengan karakteristik khusus.
3. Mendukung Lampiran: Jika pesan mengandung lampiran, "Content-Type" memberikan informasi tentang jenis konten lampiran tersebut (misalnya, PDF, gambar JPEG, dokumen Word, dll.).
4. Mendukung Format Konten: Misalnya, jika pesan mengandung bagian teks biasa dan bagian HTML, "Content-Type" akan menentukan tipe konten untuk masing-masing bagian, tergantung pada preferensi pengguna atau kemampuan klien.

#### Penjelasan MIME

Multipurpose Internet Mail Extensions atau MIME Type adalah standar internet yang menjelaskan konten file internet berdasarkan sifat dan format dokumen, file, atau kumpulan byte yang membantu browser membuka file dengan ekstensi atau plugin yang sesuai. Ini didefinisikan dan distandarisasi dalam IETF's RFC 6838.

Tipe MIME berisi dua bagian, yaitu.
1. Type, menjelaskan kategorisasi tipe MIME yang ditautkan satu sama lain.
Subtype, unik untuk tipe file tertentu yang merupakan bagian dari tipe.
2. Browser menggunakan jenis MIME, bukan ekstensi file, untuk menentukan cara memproses URL, sehingga web server harus mengirimkan jenis MIME yang benar di header jenis konten respons. Jika ini tidak dikonfigurasi dengan benar, browser mungkin salah menafsirkan konten file dan situs tidak akan bekerja dengan benar, dan file yang diunduh mungkin salah dalam penanganan.

#### Jenis-Jenis MIME Type
Ada dua kelas tipe: discrete dan multipart. Jenis diskrit adalah jenis yang mewakili satu file atau media, seperti satu teks atau file musik, atau video. Jenis multipart adalah salah satu yang mewakili dokumen yang terdiri dari beberapa bagian komponen, yang masing-masing mungkin memiliki jenis MIME tersendiri; atau, tipe multipart dapat merangkum banyak file yang dikirim bersama dalam satu transaksi. Misalnya, tipe MIME multipart digunakan saat melampirkan banyak file ke email.

Dengan pengecualian multipart/form-data, digunakan dalam metode POST pada HTML Forms, dan multipart/byteranges, digunakan dengan 206 Partial Content untuk mengirim bagian dari dokumen, HTTP tidak menangani dokumen multipart dengan cara khusus: pesan ditransmisikan ke browser.