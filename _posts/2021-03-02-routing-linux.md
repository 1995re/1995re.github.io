---
title:  "02-March-2021"
description: "Routing Linux"
comments: true
---

Blast from the past, thats what I'm thinking when I see my oldest post about linux. I took it from the book since we're doing some final exam from it' all we do it is doing some legitly a DNS server and bunch of stuff related to server in linux. Thats a while years ago in the high school.

---

Original post from my first blog : [Routing Linux](http://cyber-copas.blogspot.com/2011/08/routing-linux.html)

Setting Routing dengan Linux PC Router dengan konfigurasi Ip_forwarding, dan NAT+MASQUERADE
Installasi ini dilakukan pada distro linux redhat dan fedora core (LINUX TEXT).

1. Sebelum Setting mintalah IP publik ke ISP lengkap dengan netmask, broadcast dan dns-nya. Kemudian tentukan juga IP Lokal yang akan digunakan pada komputer client. Misal :

(eth0)
IP : 192.168.0.2
NETMASK : 255.255.255.0
GATEWAY : 192.168.0.1
BROADCAST : 192.168.0.200
NETWORK : 192.168.1.0
DNS1 : 202.134.0.155
DNS2 : 202.134.2.5

(eth1)
IP : 172.16.0.254/24
NETMASK : 255.255.0.0
BROADCAST : 172.16.0.200
NETWORK : 172.16.0.0

ingan terlebih dulu login ke username sebagai ROOT.
- Untuk melakukan perubahan tekan tomboll (insert)
- Untuk menyimpan perubahan tekan escape : wq (write quit).

2. Settinglah IP pada ethernet-0.
# vi /etc/sysconfig/network-scripts/ifcfg-eth0
ip static
DEVICE=eth0
BOOTPROTO=static
BROADCAST=192.168.0.200
IPADDR=192.168.0.2
NETMASK=255.255.255.0
NETWORK=192.168.0.0
ONBOOT=yes

dhcp
DEVICE=eth0
BOOTPROTO=dhcp
ONBOOT=yes

2. Settinglah IP MGW dan HostName, serta DNS Resolver
# vi /etc/sysconfig/network
NETWORKING=yes
HOSTNAME=router
GATEWAY=192.168.0.1

# vi /etc/resolv.conf
nameserver 202.134.0.155
nameserver 202.134.2.5


3. Settinglah IP pada ethernet-1
# vi /etc/sysconfig/network-scripts/ifcfg-eth1
DEVICE=eth1
BOOTPROTO=static
BROADCAST=172.16.0.200
IPADDR=172.16.0.1
NETMASK=255.255.0.0
NETWORK=172.16.0.0
ONBOOT=yes


Pastikan default gateway telah mengarah ke IP gateway ISP,
# route –n
Dan untuk melihat IP masing-masing ethernet cobalah command berikut :
# ifconfig|more


5. Setting IP Forwarding, agar paket dari jaringan client dapat berjalan ke jaringan di luarnya melalui gateway.
# vi /etc/sysctl.conf
rubah net.ipv4.ip_forward = 0 menjadi net.ipv4.ip_forward = 1


# chkconfig --level 2345 network on
# /etc/rc.d/init.d/network restart


Sekarang lakukan testing dengan ping ke DNS nya:
# ping 202.134.0.155 atau 202.134.2.5
Jika hasilnya Reply berarti settingnya sudah berhasil dan tinggal selangkah lagi.

6. Agar client atau jaringan lokal (LAN) yang terhubung dengan sistem linux anda (ke eth1) dapat mengakses internet, maka settinglah MGW dengan menggunakan source NAT IPTables dan Forwarding.
# /etc/init.d/iptables stop
# vi /etc/rc.d/rc.nat

--:-- Tambahkan scripts berikut --:--
# !/bin/sh
# flush
Iptables –F
Iptables –F –t nat
Iptables –nL
Iptables –X
# Script iptables untuk Source NAT sesuai dengan ip di eth0 dan eth1 (IP Statik)
/sbin/iptables -t nat -A POSTROUTING -o eth0 -s 192.168.10.0/24 -j SNAT --to-source 192.168.1.2
# Script iptables jika ip external eth0 merupakan DHCP
/sbin/iptables -t nat -A POSTROUTING -o eth0 -s 192.168.10.0/24 -j MASQUERADE
# Script Forwarding
/sbin/iptables -t nat -A PREROUTING -i eth1 -s 192.168.10.0/24 -p tcp --dport 80 -j REDIRECT --to-ports 3128
/sbin/iptables -t nat -A PREROUTING -i eth1 -s 192.168.10.0/24 -p udp --dport 80 -j REDIRECT --to-ports 3128
/sbin/iptables -t nat -A PREROUTING -i eth1 -s 192.168.10.0/24 -p tcp --dport 8080 -j REDIRECT --to-ports 3128
/sbin/iptables -t nat -A PREROUTING -i eth1 -s 192.168.10/24 -p udp --dport 8080 -j REDIRECT --to-ports 3128

# chmod +x /etc/rc.d/rc.nat
# iptables –L –t nat
# Service iptables save --> untuk simpan iptables yang kita buat.
# service iptables start/stop/restart --> jika ingin dipergunakan.
