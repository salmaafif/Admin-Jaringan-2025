# Menyambungkan VM NoGUI dan GUI

## Topologi
![image](https://github.com/user-attachments/assets/682bf163-37ef-4e5d-a37b-a6d5f6ad24ed)
Topologi ini menunjukkan dua VM yang terhubung lewat jaringan internal. VM 1 bertindak sebagai gateway dengan IP 192.168.200.1 dan terhubung ke internet melalui bridge adapter. VM 2 berperan sebagai client dengan IP 192.168.200.10/24, yang hanya terhubung ke VM 1. Agar VM 2 bisa mengakses internet, VM 1 harus mengaktifkan IP forwarding dan NAT. Singkatnya, semua koneksi dari VM 2 akan lewat VM 1 sebelum ke internet.

## VM1 (NoGUI)
1. Set interface
   - Adapter 1 = Bridge Adapter
   - Adapter 2 = Internal Network
2. Cek Interface -> ip a
3. Set IP static
   - Masuk ke bash, ketik `nano/etc/network/interfaces`
     tambahkan :
     - iface enp0s8 inet static
     - address 192.168.200.1
     - network 192.168.200.0
     - netmask 255.255.255.0
     - broadcast 192.168.200.255
     - dns-nameserves 1.1.1.1
4. Restart network
   `systemctl restart networking`
5. Install iptables
6. echo 1 > /proc/sys/net/ipv4/ip.forward
7. Tulis perintah iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
8. iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
9. iptables -A FORWARD -i enp0s3 -O ENP0S8 -j ACCEPT
10. iptable persistence
    - set named.conf & names.conf.options
    - set names.conf.external-zones. tambahkan kelompok3.com dan zone IP
    - set kelompok3.com dan zone IP

## VM2
1. Set interface
   - Adapter 1 = internal network
2. Set IP
   - dapat diakses dari settings -> wired -> ipv4
   - IPv4 method = manual
   - Address = 192.168.200.2
   - Netmask = 255.255.255.0
   - Gateway = 192.168.200.1
     ![image](https://github.com/user-attachments/assets/755e9b64-0bb1-4f3a-b49d-ea0dd70480ee)

3. DNS
   - 192.168.200.1, 1.1.1.1
