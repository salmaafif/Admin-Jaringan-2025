# Komponen Proses

Suatu proses terdiri dari ruang address dan sekumpulan struktur data di dalam kernel. Ruang alamat merupakan kumpulan halaman memori yang telah ditandai oleh kernal intik penggunaan proses.
Halaman merupakan unit dimana memori dikelola, biasanya berukuran 4KiB / 8KiB. Halaman - halaman / pages tersebut digunakan untuk menyimpan kode, data, dan tumpukan proses. Struktur data di dalam kernel melakacak status proses, prioritas, parameter penjadwalannya, dsb.

Suatu proses dibayangkan sebagai wadah untuk kumpulan sumber daya (resource) yang dikelola oleh kernel pada program yang sedang berjalan. Resource tersebut meliputi halaman memori yang menyimpan kode dan data program, deskriptor file yang merujuk ke open file, dan berbagai atribut yang menggambarkan status proses.

Struktur data internal kernel yang mencatat berbagai informasi tentang setiap proses : 
- Peta ruang alamat proses
- Status proses saat ini (berjalan, sleep, dll)
- Prioritas proses
- Informasi mengenai resource yang digunakan dalam proses (CPU, memory, dll)
- Informasi mengenai file dan port jaringan yang dibuka oleh suatu proses
- Pemilih proses (ID user)

Thread merupakan konteks eksekusi dalam sebuah proses. Sebuah proses dapat memiliki banyak Thread, dimana semuanya membagikan ruang alamat yang sama dan resource lainnya. Thread digunakan untuk mencapai paralelisme dalma sebuah proses. Thread juga dikenal sebagai proses ringan karena mudah untuk dibuah dan dihapus daripada proses.

## PID : Process ID Number
Setiap proses diidentifikasi melalui unique Process ID Number, atau PID. PID merupakan bilangan bulat / integer yang dibuat oleh kernel pada setiap proses ketika proses dibuat. PID merujuk ke proses dalam berbeagi panggilan sistem, contohnya, untuk mengirim sinyal ke proses tersebut.

## PPID : Parent Process ID Number
Setiap proses juga terkait dengan proses induk, yaitu proses yang membuatnya. Nomor ID proses induk, atau PPID, adalah PID dari proses induk. PPID digunakan untuk merujuk ke proses induk dalam berbagai panggilan sistem.

### 3. UID dan EUID: ID Pengguna dan ID Pengguna Efektif
ID pengguna, atau UID, adalah ID pengguna dari pengguna yang memulai proses. ID pengguna efektif, atau EUID, adalah ID pengguna yang digunakan proses untuk menentukan sumber daya apa yang dapat diakses oleh proses.

## Siklus Hidup Proses
Untuk membuat proses baru, sebuah proses menyalin dirinya sendiri dengan panggilan sistem fork. Fork membuat salinan dari proses asli, dan salinan itu sebagian besar identik dengan induknya. Proses baru memiliki PID yang berbeda dan memiliki informasi akuntansi sendiri.

### 1. Sinyal
Sinyal adalah cara untuk mengirim notifikasi ke sebuah proses. Mereka digunakan untuk memberi tahu proses bahwa suatu peristiwa tertentu telah terjadi. Ada sekitar tiga puluh jenis sinyal yang berbeda yang didefinisikan dan digunakan dengan berbagai cara.

### 2. Perintah kill: Mengirim Sinyal
Perintah kill paling sering digunakan untuk menghentikan sebuah proses. Kill dapat mengirim sinyal apa pun, tetapi secara default mengirim TERM. Kill dapat digunakan oleh pengguna biasa pada proses mereka sendiri atau oleh root pada proses mana pun.

## Monitoring Proses
Perintah ps adalah alat utama administrator sistem untuk memantau proses. Ps dapat menunjukkan PID, UID, prioritas, dan terminal kontrol dari proses. Anda dapat memperoleh gambaran berguna tentang sistem dengan menjalankan ps aux.

### Proses Berkala
Daemon cron adalah alat tradisional untuk menjalankan perintah pada jadwal yang telah ditentukan. Ini mulai berjalan saat sistem boot dan berjalan selama sistem aktif.
