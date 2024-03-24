 <h1 align="Center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>


<p align="center">
  <img src="img/Logo_PENS.png" alt="Logo PENS">
</p>

<h4 align="Center">Anggota Kelompok 5</h4>

<p align="center">
1. Arsyita Devanaya Arianto (3122500008) <br>
2. Mirta Chadhirotin Nachlah (3122500009) <br>
3. Shofira Izza Nurrohmah (3122500026)
</p>

<br>
<h4 align="center">
PROGRAM STUDI VOKASI <br>
D-III TEKNIK INFORMATIKA <br>
DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER 
POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br> 
2023
</h4> <br><br><hr>

Langkah-langkah instalasi DNS server dengan menggunakan aplikasi BIND9 pada Debian 12 [BIND9-debian-wiki](https://wiki.debian.org/Bind9#Debian_Bookworm) :


1. Melakukan instalasi BIND9:
   ```
   sudo apt install bind9 bind9-doc bind9-dnsutils 
   ```
   ![alt text](img/langkah1.png)

2. Berpindah ke folder /etc/bind:
   ```
   cd /etc/bind --berpindah
   ls -al --melihat isi folder
   ```
   ![alt text](img/langkah2.png)

3. Melakukan edit file named.conf:
   ```
   sudo nano named.conf
   ```
   ![alt text](img/langkah3.png)
   ACL (Access Control List) internal didefinisikan untuk mengatur akses ke jaringan yang dikelola (192.168.0.0/24). File ini memanggil 3 file lainnya yaitu named.conf.options, named.conf.local, dan named.conf.default-zones.

4. Melakukan edit file named.conf.options:
   ```
   sudo nano named.conf.options 
   ```
   ![alt text](img/langkah4.png)
   File ini berisi forwaders 1.1.1.1 dan IP yang digunakan adalah 192.168.5.1.

5. Melakukan edit file named.conf.local:
   ```
   sudo nano named.conf.local
   ```
   ![alt text](img/langkah5.png)
   Zona "kelompok5.local" adalah zona forward untuk memetakan nama ke alamat IP. File zonanya disimpan di /var/lib/bind/kelompok5.local.zone. Zona invers "5.168.192.in-addr.arpa" adalah zona invers untuk memetakan alamat IP ke nama. File invers zonanya disimpan di /var/lib/bind/kelompok5.local.inc.

6. Mengecek dengan utilitas setelah konfigurasi:
   ```
   sudo named-checkconf /etc/bind/named.conf
   ```

7. Melakukan konfigurasi zonefile, berpidah ke folder /var/lib/bind:
   ```
   cd /var/lib/bind/ --berpindah
   ls -al --melihat isi folder
   ```
   ![alt text](img/langkah7.png)

8. Melakukan edit file db.kelompok5.local:
   ```
   sudo nano db.kelompok5.local
   ```
   ![alt text](img/langkah8.png)
   Domain kelompok5.local memiliki otoritas awal (startup authority) yang terletak di host/server NS. Serialnya mengikuti pola tahun-bulan-tanggal-urutan editing. Server NS memiliki alamat internet di 1. Alias DNS (CNAME) untuk www ditujukan ke NS.


9.  Melakukan edit file db.kelompok5.local.inv:
    ```
    sudo nano db.kelompok5.local.inv
    ```
   
    ![alt text](img/langkah9.png)
   Yang membedakan dengan db.kelompok5.local adalah IN, PTR, NS.
10. Mengecek dengan utilitas setelah konfigurasi:
    ```
    named-checkzone kelompok5.local db.kelompok5.local 
    ```
    ![alt text](img/langkah10.png)

11. Mengecek dengan utilitas setelah konfigurasi:
    ```
    named-checkzone 5.168.192.inaddr-arpa db.kelompok5.local.inv  
    ```
    ![alt text](img/langkah11.png)

12. Melakukan edit file resolve.conf:
    ```
    sudo nano /etc/resolv.conf
    ```
    ![alt text](img/langkah12.png)
    

13. Menjalankan service named:
    ```
    sudo systemctl restart named
    ```

14. Melihat status service named:
    ```
    sudo systemctl status named
    ```
    ![alt text](img/langkah14.png)

15. Menjalankan perintah untuk melakukan pengetesan:
    ```
    dig kelompok5.local 
    ```
    ![alt text](img/langkah15.png)

16. Menjalankan perintah untuk melakukan pengetesan:
    ```
    dig -x 192.168.5.1
    ```
    ![alt text](img/langkah16.png)

17. nslookup ns digunakan untuk mencari informasi NS (Name Server) dari suatu domain.
    ```
    nslookup ns.kelompok5.local
    ```
    ![alt text](img/langkah17.png)



   
