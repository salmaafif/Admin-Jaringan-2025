# Menyambungkan VM NoGUI dan GUI

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
3. DNS
   - 192.168.200.1, 1.1.1.1
