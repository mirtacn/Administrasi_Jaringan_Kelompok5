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

---

# NTP Server

1.  Lakukan instalasi paket layanan sinkronisasi waktu → `sudo apt install systemd-timesyncd`
    > ![alt text](assets/image-1.png)

2.  Melakukan konfigurasi timezone ke Asia/Jakarta → `sudo timedatectl set-timezone Asia/Jakarta`
    > ![alt text](assets/image-1.png)

3.  Melakukan konfigurasi Real Time Clock (RTC) untuk merefer ke UTC (Coordinated Universal Time) → `sudo timedatectl set-local-rtc false`
    > ![alt text](assets/image-1.png)

4.  Mengaktifkan NTP Client untuk sinkronisasi waktu → `sudo timedatectl set-ntp true`
    > ![alt text](assets/image-1.png)

5.  Menyunting file timesyncd.conf untuk mengarah ke NTP server terdekat untuk mendapatkan waktu delay terpendek. Biasanya setiap organisasi atau negara mempunyai NTP Server sendiri → `sudo nano /etc/systemd/timesyncd.conf`
    > ![alt text](assets/image-1.png)

6.  Restart layanan sinkronisasi waktu dan pastikan layanan berjalan dengan benar

        `sudo systemctl restart systemd-timesyncd`

    > ![alt text](assets/image-1.png)
Mengecek status layanan sinkronisasi waktu → `sudo systemctl status systemd-timesyncd`
    > ![alt text](assets/image-1.png)
Dapat dilihat status active(running)

7.  Lakukan pengecekan kesesuaian tanggal system dengan perintah → `timedatectl`
    > ![alt text](assets/image-1.png)

Menampilkan status sinkronisasi waktu pada sistem dengan server NTP (Network Time Protocol) → `sudo timedatectl timesync-status`

    > ![alt text](assets/image-1.png)

Bisa dilihat sudah tersambung ke NTP 0.id.pool.ntp.org, dan memiliki delay waktu yang terbilang cukup kecil yaitu +- 30ms

# Apache 2 dan PHP-FM

## Install Apache2

1.  Install Apache2 → `sudo apt -y install apache2`
    > ![alt text](assets/image-1.png)

2.  Melakukan konfigurasi Apache2

- `sudo nano /etc/apache2/conf-enabled/security.conf`  
    > ![alt text](assets/image-1.png)

  Mengganti line 12 --> `ServerTokens Prod` --> berarti Apache hanya akan menampilkan informasi identifikasi server yang minimal dalam header responsnya.

- `sudo nano /etc/apache2/mods-enabled/dir.conf`
    > ![alt text](assets/image-1.png)

  Menambahkan nama file yang hanya bisa diakses dengan nama direktori, yaitu index.html, index.htm, dan index.php

- `sudo nano /etc/apache2/apache2.conf`
    > ![alt text](assets/image-1.png)

  Line 70 --> Menambahkan specify server name

- `sudo nano /etc/apache2/sites-enabled/000-default.conf`
    > ![alt text](assets/image-1.png)

  Mengganti line 11 --> Mengganti webmaster's email

- `systemctl reload apache2`
    > ![alt text](assets/image-1.png)

  Melakukan reload layanan apache

3.  Melakukan test ke web browser
    > ![alt text](assets/image-1.png)

## Install PHP 8.2

1.  Melakukan install PHP versi 8.2 beserta modul mbstring dan paket pear --> `sudo apt -y install php8.2 php8.2-mbstring php-pear`
    > ![alt text](assets/image-1.png)

2.  Mengecek php version → `php -v`
    > ![alt text](assets/image-1.png)
    Karena sudah muncul version dari php, berarti php telah berhasil terinstall

3.  Melakukan test terhadap php

    - `nano php_test.php`
    > ![alt text](assets/image-1.png)

      Membuat file php_test.php, yang akan mencetak ouytput dari `php -i` ketika dijalankan

      - Jalankan `php php_test.php | head`
    > ![alt text](assets/image-1.png)
        Akan menampilkan output dari `php -i` yaitu menampilkan informasi terkait konfigurasi PHP

4.  Melakukan Install PHP-FM → `sudo apt -y install php-fpm`
    > ![alt text](assets/image-1.png)

5.  Mengkonfigurasi PHP-FM pada file konfigurasi Apache - `sudo nano /etc/apache2/sites-available/default-ssl.conf`
    > ![alt text](assets/image-1.png)

    Menambahkan diantara tag < VirtualHost> - < /VirtualHost> yaitu mengatur Apache HTTP Server agar dapat meneruskan permintaan PHP ke PHP-FPM (PHP FastCGI Process Manager)

    - `sudo a2enmod proxy_fcgi setenvif`
    > ![alt text](assets/image-1.png)
    
      digunakan untuk mengaktifkan modul-modul proxy_fcgi dan setenvif dalam server Apache.

    - `sudo a2enconf php8.2-fpm`
     ![alt text](assets/image-1.png)
      digunakan untuk mengaktifkan modul-modul php8.2-fpm

    - `sudo systemctl restart php8.2-fpm apache2`
    > ![alt text](assets/image-1.png)
      Melakukan restart service php8.2-fpm dan apache2

6.  Melakukan test validasi terhadap PHP-FM dengan membuat file info.php di root document → `sudo nano /var/www/html/info.php`
    > ![alt text](assets/image-1.png)
    Membuat file info.php yang nanti nya outputnya akan menjalankan command `phpinfo()`

7.  Melakukan test di browser, membuka file info.php di browser
    > ![alt text](assets/image-1.png)
    Jika berhasil, maka akan menampilkan semua informasi terkait php.

# MariaDB & PhpMyAdmin

## Install MariaDB

1.  Melakukan install mariadb-server --> `sudo apt -y install mariadb-server`
    > ![alt text](assets/image-1.png)
2.  `sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf`
    > ![alt text](assets/image-1.png)
    Pada line 95 --> Mengkonfirmasi default charset menggunakan utf8mb4.

3.  `sudo systemctl restart mariadb`
    > ![alt text](assets/image-1.png)
    Melakukan restart service mariadb

4.  Inisial Konfigurasi dan testing database MariaDB Server - `sudo mysql_secure_installation`
    > ![alt text](assets/image-1.png)
    Melakukan beberapa tindakan keamanan standar dalam instalisasi MariaDB, Ditahap ini akan di beri beberapa pertanyaan keamanan. Seperti set MariaDB root password, remove anonymous users, dll.

    - Connect to MariaDB → `sudo mysql`
    > ![alt text](assets/image-1.png)
    - Menampilkan hak akses yang dimiliki oleh user root → `show grants for root@localhost;`
    > ![alt text](assets/image-1.png)

    - Menampilkan semua daftar user → `select user,host,password from mysql.user;`
    > ![alt text](assets/image-1.png)

    - show database list → `show databases;`
    > ![alt text](assets/image-1.png)

    - create test database → `create database test_database;`
    > ![alt text](assets/image-1.png)

    - create test table on test database → `create table test_database.test_table (id int, name varchar(50), address varchar(50), primary key (id));`
    > ![alt text](assets/image-1.png)

    - insert data to test table → `insert into test_database.test_table(id, name, address) values("001", "Debian", "Hiroshima");`
    > ![alt text](assets/image-1.png)

    - show test table → `select * from test_database.test_table;`
    > ![alt text](assets/image-1.png)

    - delete test database → `drop database test_database;`
    > ![alt text](assets/image-1.png)

## Install PhpMyAdmin

1.  Melakukan install phpmyadmin --> `sudo apt install phpmyadmin`
2.  Pilih Apache2 sebagai web server
    > ![alt text](assets/image-1.png)

3.  Pilih **yes** agar konfigurator melakukan langkah-langkah yang diperlukan untuk membuat database dan pengguna khusus untuk phpMyAdmin agar dapat berfungsi dengan baik.
    > ![alt text](assets/image-1.png)

4.  Masukkan password phpmyadmin
    > ![alt text](assets/image-1.png)
    > ![alt text](assets/image-1.png)

5.  Menambahkan konfigurasi phpmyadmin di apache2 → `sudo nano /etc/apache2/apache2.conf`
    > ![alt text](assets/image-1.png)
    Mendaftarkan file `/etc/phpmyadmin/apache.conf`

6.  Coba membuka phpmyadmin di web browser    
  > ![alt text](assets/image-1.png)
  > ![alt text](assets/image-1.png)

7.  Menambahkan privillege ke user phpmyadmin - Login ke mariadb → `sudo mariadb -u root -p` - Lalu berikan hak akses penuh kepada user phpmyadmin → `GRANT ALL PRIVILEGES ON *.* TO 'phpmyadmin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION; FLUSH PRIVILEGES;`
    > ![alt text](assets/image-1.png)
    > ![alt text](assets/image-1.png)

    Bisa dilihat sekarang user phpmyadmin, memiliki hak akses penuh seperti create database, dll.

# Email System

## POSTFIX : SMTP Server (TCP 25)

1.  Melakukan install postfix sasl2-bin --> `sudo apt -y install postfix sasl2-bin`
2.  Pilih no configuration, karena kita akan melakukan konfigurasi secara manual
    > ![alt text](assets/image-1.png)

3.  Mencopy file /usr/share/postfix/main.cf.dist ke /etc/postfix/main.cf --> `sudo cp /usr/share/postfix/main.cf.dist /etc/postfix/main.cf`
    > ![alt text](assets/image-1.png)

4.  `sudo nano /etc/postfix/main.cf` - Uncoment line 82
    > ![alt text](assets/image-1.png)
    - Uncoment line 98 dan isi dengan email hostname kelompok5
    > ![alt text](assets/image-1.png)

    - Uncoment line 106 dan isi dengan hostname kelompok5
    > ![alt text](assets/image-1.png)

    - Uncoment line 127
    > ![alt text](assets/image-1.png)

    - Uncoment line 141
    > ![alt text](assets/image-1.png)

    - Uncoment line 189
    > ![alt text](assets/image-1.png)

    - Uncoment line 232
    > ![alt text](assets/image-1.png)

    - Uncoment line 277
    > ![alt text](assets/image-1.png)

    - Uncoment line 294 dan tambahkan local network
    > ![alt text](assets/image-1.png)

    - Uncoment line 416
    > ![alt text](assets/image-1.png)

    - Uncoment line 427
    > ![alt text](assets/image-1.png)

    - Uncoment line 449
    > ![alt text](assets/image-1.png)

    - Comment line 558 dan tambahkan di line 589 konfigurais smtpd_banner
    > ![alt text](assets/image-1.png)

    - Tambahkan di line 659 sendmail_path
    > ![alt text](assets/image-1.png)

    - Tambahkan di line 664 newaliases_path
    > ![alt text](assets/image-1.png)

    - Tambahkan di line 669 mailq_path
    > ![alt text](assets/image-1.png)

    - Tambahkan di line 675 setgid_group
    > ![alt text](assets/image-1.png)

    - Comment line 679
    > ![alt text](assets/image-1.png)

    - Comment line 683
    > ![alt text](assets/image-1.png)

    - Comment line 688
    > ![alt text](assets/image-1.png)

    - Comment line 692
    > ![alt text](assets/image-1.png)

    - Tambahkan internet protocol di line 692
    > ![alt text](assets/image-1.png)

    - Menambahkan config di line terakhir. Yaitu mematikan SMTP VRFY command, require HELO command to sender hosts, Mengatur limit an email size, dan mengatur SMTP-Auth settings
    > ![alt text](assets/image-1.png)

5.  Meng-update database alias untuk sistem postfix --> `sudo newaliases`
    > ![alt text](assets/image-1.png)

6.  Melakukan restart layanan postfix --> `systemctl restart postfix`
    ![](https://lh7-us.googleusercontent.com/bXXqd7RYLVUOOmnV3iavykYYxya3fQT3Iwjy89N1svFEAy9DYfQrHGpo5f5tlvfo9Rl0uoHeSFEgnSHIx5K6_NcBcX_MV2SLuwxIVkYyMcIvfxq5bf0WnRts5oHifYCOcBF9369MV-R_Uxr0sHBagGg)

7.  Menambahkan konfigurasi anti spam

    - `sudo nano /etc/postfix/main.cf`
    > ![alt text](assets/image-1.png)

    - Melakukan restart layanan postfix --> `sudo systemctl restart postfix`
    > ![alt text](assets/image-1.png)

## Install **DOVECOT : IMAP4 (TCP 143) and POP3 (TCP110)**

1.  Melakukan install dovecot-core, dovecot-pop3d, dovecot-imapd --> `sudo apt -y install dovecot-core dovecot-pop3d dovecot-imapd`
    > ![alt text](assets/image-1.png)

2.  `sudo nano /etc/dovecot/dovecot.conf`
    > ![alt text](assets/image-1.png)
    Uncoment line 30 agar Dovecot mendengarkan koneksi pada semua antarmuka jaringan yang tersedia.

3.  `sudo nano /etc/dovecot/conf.d/10-auth.conf`
    > ![alt text](assets/image-1.png)

    Uncoment line 10 dan izinkan plain text auth - Tambahkan auth_mechanisms di line 100
    > ![alt text](assets/image-1.png)

4.  `sudo nano /etc/dovecot/conf.d/10-mail.conf`
    ![](https://lh7-us.googleusercontent.com/    > ![alt text](assets/image-1.png)
    Ubah mail location di line30 menjadi Maildir

5.  `sudo nano /etc/dovecot/conf.d/10-master.conf`
    > ![alt text](assets/image-1.png)
    Tambahkan Postfix smtp-auth di line 107 - 109

6.  Restart layanan dovecot --> `sudo systemctl restart dovecot`
    > ![alt text](assets/image-1.png)

# Final Check All Services

1.  `netstat -a| grep LISTEN`
    > ![alt text](assets/image-1.png)
    Akan terlihat hasilnya dengan status Server (LISTEN) : MariaDB(MySQL), IMAP, POP3, DNS(domain - http), IMAPS, POP3S, SSH, Postfix (SMTP)

2.  Melakukan Cek terhadap Layanan Posfix `telnet mail.kelompok5.local 25`
    > ![alt text](assets/image-1.png)
    Memeriksa apakah server mail.kelompok5.local dapat menerima koneksi pada port 25. Lalu menhalankan command `ehlo mail.kelompok5.local` yang digunakan untuk memberikan informasi tentang kemampuan server, seperti fitur-fitur yang didukung atau batasan konfigurasi.

# Thunderbird Email GUI Client

1.  Melakukan install Thunderbird melalui flatpak --> `flatpak install flathub org.mozilla.Thunderbird`
    > ![alt text](assets/image-1.png)

2.  Menginstall thunderbird GUI dari https://flathub.org/apps/org.mozilla.Thunderbird
    > ![alt text](assets/image-1.png)

3.  Menambahkan 2 akun email ( yaitu user mirta dan root )
    > ![alt text](assets/image-1.png)

4.  Mencoba saling send email - User root mencoba send email ke user mirta
    > ![alt text](assets/image-1.png)

    - User mirta mengek email yang diterima
    > ![alt text](assets/image-1.png)

**Additional :** Untuk melakukan penambahan akun email anda dapat melalui terminal dengan command yang sama saat melakukan penambahan user. `sudo adduser <namauser>`. Nantinya anda akan disuruh mengisi informasi terkait user tersebut.

# Roundcube Webmail

1.  Membuat database yang nantinya digunakan untuk roundcube
    > ![alt text](assets/image-1.png)

2.  Melakukan Install dan konfigurasi RoundCube - Melakukan install roundcube -->`sudo apt -y install roundcube roundcube-mysql`
    pilih no karena akan melakukan konfigurasi secara manual
    > ![alt text](assets/image-1.png)
    > ![alt text](assets/image-1.png)

3.  Masuk ke directory roundcube --> `cd /usr/share/dbconfig-common/data/roundcube/install`
    > ![alt text](assets/image-1.png)

4.  Mengimpor file mysql ke dalam database roundcube dengan menggunakan akun pengguna (-u roundcube) dan database (-D roundcube) yang sesuai. --> `sudo mysql -u roundcube -D roundcube -p < mysql`
    dan masukkan password mariaDB user roundcube (password)  
    > ![alt text](assets/image-1.png)

5.  Melakukan set database informasi --> `sudo nano /etc/roundcube/debian-db.php`
    > ![alt text](assets/image-1.png)

6.  `sudo nano /etc/roundcube/config.inc.php`
    > ![alt text](assets/image-1.png)
    Melakukan konfigurasi imap_host, smtp_host, smtp user dan password

7.  `sudo nano /etc/apache2/conf-enabled/roundcube.conf`
    > ![alt text](assets/image-1.png)
    Mengatur agar ketika membuka path /roundcube di domain kita, akan di arahkan ke dirctory /var/lib/roundcube.

8.  Melakukan restart service apache2 --> `sudo systemctl restart apache2`
9.  Mencoba membuka roundcube di web browser (domain/roundcube)
    > ![alt text](assets/image-1.png)
    > ![alt text](assets/image-1.png)

10. Mencoba send email
    User 1 mengirim email ke user mirta
    > ![alt text](assets/image-1.png)
    Pesan berhasil terkirim :
    > ![alt text](assets/image-1.png)

    User mirta mengecek email yang diterima :
    > ![alt text](assets/image-1.png)
