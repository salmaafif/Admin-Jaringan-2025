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

