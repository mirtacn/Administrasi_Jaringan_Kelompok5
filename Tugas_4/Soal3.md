# Bagaimana Cara kerja dari iterative dan recursive dari DNS Query, ada 8 step, dari PC anda! misal akses detik.com

Iteratif dan rekursif adalah dua mode pencarian yang berbeda yang digunakan dalam proses DNS (Domain Name System) query. Berikut adalah langkah-langkah bagaimana keduanya bekerja dalam skenario pencarian DNS dari PC untuk mengakses detik.com:

1. **Pengaturan Permintaan Awal**: PC akan mengirim permintaan DNS pertama ke resolver DNS lokal, seperti yang dikonfigurasi pada perangkat atau router.

### Mode Iteratif:

2. **Permintaan Resolver**: Resolver DNS lokal akan mengirim permintaan ke server DNS tertentu untuk mengetahui alamat IP dari detik.com. Server DNS yang dituju bisa menjadi server otoritatif untuk domain detik.com atau server DNS lain yang resolver kenal.

3. **Respons dari Server DNS**: Server DNS akan memberikan balasan kepada resolver dengan informasi yang diminta. Jika server tersebut adalah server otoritatif untuk detik.com, maka akan memberikan alamat IP langsung. Namun, jika tidak, maka server tersebut akan memberikan informasi tentang server DNS lain yang mungkin tahu tentang detik.com.

4. **Permintaan Selanjutnya (Iteratif)**: Resolver DNS akan mengirim permintaan ke server DNS yang disarankan oleh server sebelumnya. Proses ini berulang sampai resolver menerima alamat IP detik.com atau sampai tidak ada lagi server DNS yang disarankan.

### Mode Rekursif:

2. **Permintaan Resolver**: Resolver DNS lokal akan mengirim permintaan ke server DNS lokal, biasanya milik penyedia layanan internet (ISP), untuk mengetahui alamat IP detik.com.

3. **Server DNS Melakukan Pencarian**: Server DNS lokal akan mencoba menemukan alamat IP detik.com. Jika server ini tidak memiliki informasi tersebut di cache-nya, ia akan mulai mencari tahu informasi tersebut.

4. **Server DNS Menghubungi Server Lain**: Jika server DNS lokal tidak memiliki informasi yang diperlukan di cache-nya, ia akan menghubungi server DNS lain untuk mencari tahu informasi tersebut.

5. **Iterasi Pencarian**: Proses ini berlanjut melalui serangkaian permintaan dan respon antara server DNS lokal dan server lainnya sampai alamat IP detik.com ditemukan.

6. **Informasi Dikirim Kembali ke Resolver**: Setelah alamat IP detik.com ditemukan, informasi tersebut dikirimkan kembali ke resolver DNS lokal yang awal.

7. **Resolver Mengirimkan Informasi ke PC**: Resolver DNS lokal akan mengirimkan informasi tersebut ke PC.

8. **Akses ke Situs Web**: Sekarang, dengan alamat IP detik.com diterima, PC dapat menggunakan informasi tersebut untuk mengakses situs web detik.com.
