# Laporan Workshop Administrasi Jaringan

Nama : Salma Afifa Azis
Kelas : D4 IT A
NRP : 3123600017

A. Analisis Wireshark

a.	Download http.cap dan jalankan di wireshark
 ![image](https://github.com/user-attachments/assets/d7eeb76e-5f1c-45c6-8f64-ae60840e1c34)  
 
- Versi http yang digunakan: http versi 1.1
-	IP address client : 145.254.160.237
-	IP address server : 65.208.228.223
-	Waktu client mengirimkan : 0.911310
-	Waktu server menerima : pada detik ke 4.846969 dan 3.9256900 sejak request dikirimkan.
 ![image](https://github.com/user-attachments/assets/f024dbfa-0c82-405f-95e2-543fdb93dbb3)  

B.	Analisis gambar

 ![image](https://github.com/user-attachments/assets/326f45c4-b8c0-4c3b-b0a9-392e2e6d1105)  

1.	Node to Node 
Terdapat pada lapisan Data Link Layer (layer 2 Osi)
Langkah pertama dalam pengiriman data, dimana data dikirim antara dua node yang terhubung langsung dalam jaringan. Data dikirim dalam bentuk frame dan melibatkan perangkat seperti switch atau hub. Lapisan ini bertanggung jawab untuk mengirimkan dan memastikan keandalan transmisi data antara node yang berdekatan.
2.	Host to Host (Network Layer)
Terdapat pada lapisan Network layer pada Osi
Setelah data dikirim dari node ke node, data kemudian diarahkan dari sumber ke tujuan. Lapisan ini bertanggung jawab untuk routing paket data melalui jaringan yang mungkin berbeda dan melibatkan beberapa hop.
3.	Process to Process
Terdapat pada lipas Transport Layer dalam model OSI.
Setelah data mencapai host tujuan, data kemudian dikirim ke proses atau aplikasi yang sesuai di host tersebut. Lapisan ini memastikan bahwa data yang dikirim secara andal dan dalam urutan yang benar ke proses yang dituju. Protokol seperti TCP dan UDP beroperasi dalam lapisan ini
C.	Review TCP/IP
-	Lapisan dalam TCP/IP
a.	Application Layer -> Lapisan aplikasi
Fungsi : menyediakan antarmuka untuk aplikasi jaringan seperti web, browser, email, client, dan aplikasi lainnya.
Protokol : HTTP, FTP, SMTP, DNS, dll
b.	Transport Layer
Fungsi : menjamin pengiriman data yang andal antara proses atau aplikasi di host yang berbeda
Protokol : TCP dan UDP
c.	Internet Layer
Fungsi : mengatur pengiriman paket data melalui jaringan, termasuk routing dan pengalamatan
Protokol : IP, ICMP, ARP, dll
d.	Network Access Layer
Fungsi : mengatur pengiriman data antara perangkat ddalam jaringan lokal (LAN)
Protokol : Ethernet, WiFi, PPP, dll


-	Tahap komunikasi menggunakan TCP/IP
a.	Tahap Establishment (Pembentukan Koneksi)
Biasa dikenal sebagai Three-Way-Handshake dan bertujuan membangun koneksi yang andal antara dua host (client server) sebelum pertukaran data dimulai.
SYN (syncronize) = Client mengirimkan paket SYN ke server untuk meminta pembukaan koneksi. Paket ini berisi nomor urut acak yang akan digunakan oleh client.

SYN-ACK (synchronize – acknowledge) = Server merespons dengan paket SYN-ACK. Paket ini berisi ACK konfirmasi bahwa server menerima paket SYN dari client. SYN nomor urut acak yang akan digunakan oleh server.

ACK = Client mengirimkan paket ACK ke server untuk mengonfirmasi bahwa koneksi telah terbentuk. Setelah ini, koneksi TCP terbentuk dan kedua pihak siap untuk bertukar data. 

-	Tahap Transfer Data
Setelah koneksi terbentuk, data dapat ditransfer antara client dan server. Proses transfer data:
a.	Pengiriman data : 
Data dibagi menjadi segmen – segmen kecil dan setiap segmen diberi nomor urut (seq number) untuk memastikan pengurutan yang benar.
b.	ACK :  
Penerima mengirimkan ack untuk setiap segmen yang berhasil diterima. Jika pengirim tidak menerima ACK dalam waktu tertentu, segmen akan dikirim ulang (retransmission).
c.	Flow Control :
TCP menggunakan mekanisme flow control untuk menghindari kelebihan data yang dikirim ke penerima. Penerima mengirimkan informasi tentang ukuran buffer yang tersedia kepada pengirim.
d.	Error Checking:
Setiap segmen dilengkapi dengan checksum untuk mendeteksi kesalahan selama transmisi.

-	Tahap Termination
Digunakan untuk menutup koneksi TCP secara aman setelah transfer data selesai. Biasa dikenal Four Way Handshake.
a.	FIN (finish) :
Salah satu pihak mengirimkan paket FIN untuk mengindikasikan bahwa tidak ada lagi data yang akan dikirim
b.	ACK :
Pihak lain merespons dengan paket ACK untuk mengonfirmasi penerimaan paket FIN
c.	FIN : 
Server juga mengirimkan paket FIN untuk mengindikasikan bahwa server siap menutup koneksi.
d.	ACK : 
Client merespons dengan paket ACK untuk mengonfirmasi penerimaan paket FIN dari server
Setelah ini, koneksi TCP ditutup
 
