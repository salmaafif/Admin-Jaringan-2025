# DNS SERVER

## BIND : Configure to Internal Network
#### 1. Install BIND
Menggunakan perintah `apt -y install bind9 bund9utils` 
![image](https://github.com/user-attachments/assets/bd157d46-b07a-4c8c-819f-60bfbe434da2)
#### 2. Konfigurasi BIND ke dalam Internal Network.
Menggunakan perintah `vi /etc/bind/named.conf`

![image](https://github.com/user-attachments/assets/9fe31b2b-8719-4a3e-a29e-63792673fd1a)
Kemudian mengaturnya di `/etc/bind/named.conf.internal-zones`

![image](https://github.com/user-attachments/assets/71ec6029-998a-4567-8164-2ee130d5ac5c)

`vi /etc/default/named`

![image](https://github.com/user-attachments/assets/b31ac3e2-cdab-4fcc-8b85-5942396e69ef)
#### 3. Konfigurasi File Zones untuk Setiap Zone yang telah di set

## BIND : Configure to External Network
