# 3. Mengubah Alamat IP Dinamis Menjadi Statis 

Untuk melakukan setting network di debian, kita memiliki dua cara yaitu melalui GUI (Network Manager) dan CLI (Menggunakan file /etc/network/interfaces).

Default Gateway :

![alt text](img/0.jpg)

#### A. NETWORK MANAGER
- Buka Network Manager (Anda bisa mencari "Network" di menu atas atau menggunakan perintah "nm-connection-editor" di terminal).
![alt text](img/9.png)
- Pilih interface yang terhubung/sambungkan terlebih dahulu.
![alt text](img/1.jpg)
- Buka setting pada interface tersebut.
- Pilih menu IPV4 lalu klik manual. Kemudian, masukkan konfigurasi alamat IP
<br> Address : 10.0.2.100
<br> Netmask : 255.255.255.0
<br> DNS : 8.8.8.8
<br> Lalu Klik Apply
![alt text](img/2.jpg)

#### B. Menggunakan interfaces File:

- Buka terminal.
- Buat file /etc/network/interfaces menggunakan text editor seperti nano atau vim.
![alt text](img/4.jpg)
- Isi file dengan konfigurasi yang diinginkan. Contoh:
![alt text](img/5.jpg)
- Simpan file dan keluar dari text editor.
- Jalankan perintah "sudo ifdown eth0" (gantikan "eth0" dengan nama interface yang ingin diatur) untuk mematikan interface. Lalu, Jalankan perintah "sudo ifup eth0" untuk mengaktifkan kembali interface dengan pengaturan yang baru.
![alt text](img/6.jpg)
- Kemudian cek menggunakan ~$ ip addr
![alt text](img/7.jpg)
- Lakukan pengujian!
![alt text](img/8.jpg)

Setelah melakukan salah satu cara di atas, pengaturan network di debian akan berubah sesuai dengan yang kita inginkan.