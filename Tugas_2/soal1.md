

## 1. Linux Directory Structure

Berdasarkan referensi https://www.debianadmin.com/linux-directory-structure-overview.html, Perbedaan antara Linux dan Windows terutama terletak pada struktur direktori dan format aksesnya. Berikut adalah beberapa poin penting:

1. **Format Akses Direktori**:
   - **Windows**: Menggunakan format seperti `D:\Folder\subfolder\file.txt`.
   - **Linux**: Menggunakan format seperti `/Folder/subfolder/file.txt`.

2. **Garis Miring**:
   - **Windows**: Menggunakan garis miring terbalik (`\`) dalam jalur direktori.
   - **Linux**: Menggunakan garis miring ke depan (`/`).

3. **Nama Drive**:
   - **Windows**: Menggunakan nama drive (misalnya, C:, D:).
   - **Linux**: Tidak mengenal penggunaan nama drive; semuanya berada di bawah sistem file root ("/").

4. **Struktur Direktori Linux**:
   - Mengikuti prinsip Struktur Hierarki Sistem File (FHS).
   - Semua direktori disusun hierarkis di bawah sistem file root ("/").
   - Meskipun ada variasi di beberapa distribusi, umumnya mengikuti standar yang ditetapkan oleh Free Standards Group.

5. **Perhatian terhadap Huruf Besar-Kecil**:
   - Di Linux, file dan folder memperhatikan huruf besar-kecil. Misalnya, `Folder/subfolder/file.txt` berbeda dengan `/folder/subfolder/file.txt`.

Jadi, secara singkat, Linux lebih fleksibel dalam struktur direktorinya dan tidak tergantung pada nama drive. 

Berikut adalah berbagai direktori Hirarki Sistem File Linux :

1. "**/root**"
   
    - Direktori root untuk seluruh struktur.
    - Partisi di mana / (direktori root) ditempatkan pada sistem yang kompatibel dengan UNIX atau UNIX.

2. "**/boot**"

    Berisi file Boot loader seperti Grub atau Lilo, file konfigurasi Kernel, initrd, dan system.map.

3. "**/sys**"
	
    Berisi file terkait Kernel, Firmware, dan sistem.

4. "**/sbin**"
	
    Berisi Biner Sistem dan alat Administrasi Sistem yang penting untuk operasi dan kinerja sistem.

5. "**/bin**"

	Berisi biner penting bagi pengguna dan utilitas yang diperlukan dalam mode pengguna tunggal, seperti cat, ls, dan cp.

6. "**/lib**"

	Berisi file perpustakaan untuk semua binari yang disimpan di direktori /sbin & /bin.

7. "**/dev**"

	Direktori ini mengandung sistem file dan driver yang penting.

8. "**/etc**"

	- Berisi file konfigurasi sistem penting, termasuk /etc/hosts, /etc/resolv.conf, nsswitch.conf, dan file konfigurasi jaringan.
    - Sebagian besar adalah file konfigurasi sistem dan aplikasi khusus host.

9. "**/home**"

	- Semua direktori home pengguna disimpan di bawah direktori ini, kecuali direktori home root yang disimpan di /root.
    - Direktori ini menyimpan file pengguna dan pengaturan pribadi seperti .profile.

10. "**/media**"

	Titik pemasangan umum untuk media yang dapat dipindahkan seperti CD-ROM, USB, dan disket.

11. "**/mnt**"

	- Titik pemasangan umum untuk sistem file sementara.
    - Berguna khususnya ketika memecahkan masalah dari CD-ROM, dll., di mana Anda mungkin harus memasang sistem file Root dan mengedit konfigurasi.

12. "**/opt**"

	- Direktori yang jarang digunakan di Linux untuk Paket Perangkat Lunak Opsional.
    - Banyak digunakan di OS UNIX seperti Sun Solaris, di mana paket perangkat lunak diinstal.

13. "**/usr**"

	- Sub-hierarki ke sistem file root yang merupakan direktori data pengguna
    - Berisi utilitas dan aplikasi khusus pengguna.
    - Anda akan menemukan banyak sistem file penting tetapi tidak penting yang dipasang di sini.
    -  Direktori ini mencakup:
        - **/usr/sbin**: Berisi biner sistem dan utilitas jaringan yang tidak penting dan tidak kritis.
        - **/usr/bin**: Berisi biner perintah non-esensial dan non-kritis untuk pengguna.
        - **/usr/lib**: File perpustakaan untuk binari di direktori /usr/bin & /usr/sbin.
        - **usr/share**: Direktori data bersama yang tidak bergantung pada platform.
        - **usr/local**: Sub-hierarki di bawah direktori /usr yang memiliki data spesifik sistem lokal, termasuk biner pengguna dan sistem serta perpustakaannya.

14. "**/var**"

	- Direktori /var sebagian besar dipasang sebagai sistem file terpisah di bawah root.
    - Berisi semua konten variabel seperti log, file spool untuk printer, crontab, pekerjaan, mail, proses yang berjalan, mengunci file, dll.
    - Harus hati-hati dalam merencanakan sistem file dan pemeliharaan karena ini dapat terisi cukup cepat dan ketika sistem file penuh dapat menyebabkan masalah operasional sistem dan aplikasi.

20. "**/tmp**"

	- Sistem file sementara yang menyimpan file-file sementara yang dibersihkan saat sistem di-boot ulang.
    - Ada juga direktori /var/tmp yang juga menyimpan file-file sementara.
    - Satu-satunya perbedaan antara keduanya adalah direktori /var/tmp menyimpan file yang dilindungi saat sistem di-boot ulang. Dengan kata lain, file /var/tmp tidak dihapus saat reboot.

21. "**/proc**"

    /proc adalah sebuah virtual file sistem yang berada di memori dan dipasang di bawah root. Fungsinya adalah untuk menyimpan statistik tentang proses dalam format file teks.


### LINUX DIRECTORY STRUCTURE VISUAL VIEW

Berikut adalah gambar visual dalam bentuk tree dari directory root :<br>
    <space> <img src="img/screenshoot debian.png" alt="Screenshoot debian" style="width: 70%;">

Berikut adalah gambar struktur Direktori Linux dalam Tampilan Visual :<br> 
    <space> <img src="img/Mind Map Jaringan.jpg" alt="Screenshoot debian" style="width: 90%;">