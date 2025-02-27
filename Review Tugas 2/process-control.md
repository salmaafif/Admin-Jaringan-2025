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

