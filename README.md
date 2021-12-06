# Jarkom-Modul-5-IUP1-2021

Setelah kalian mempelajari semua modul yang telah diberikan, Luffy ingin meminta bantuan untuk terakhir kalinya kepada kalian. Dan kalian dengan senang hati mau membantu Luffy.

## A. Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Luffy dibawah ini:

#### Keterangan : 

Doriki adalah DNS Server

Jipangu adalah DHCP Server

Maingate dan Jorge adalah Web Server

Jumlah Host pada Blueno adalah 100 host

Jumlah Host pada Cipher adalah 700 host

Jumlah Host pada Elena adalah 300 host

Jumlah Host pada Fukurou adalah 200 host

![VLSM_Subnetting](https://user-images.githubusercontent.com/61174498/144734892-29fd30f0-6691-47c5-8e0e-2ed10c86dfd7.png)

## B. Karena kalian telah belajar subnetting dan routing, Luffy ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM.

![Screenshot (10414)](https://user-images.githubusercontent.com/61174498/144734639-19c46d59-be52-4bcb-8175-d2b111b67827.png)

| Subnet | Node | IP | Subnet Mask | Length |
| --- | --- | --- | --- | --- |
| A | WATER7 | 10.38.7.1 | 255.255.255.128 | /25 |
| A | Blueno | 10.38.7.2 | 255.255.255.128 |  |
| B | WATER7 | 10.38.7.129 | 255.255.255.248 | /29 |
| B | Doriki | 10.38.7.130 | 255.255.255.248 |  |
| B | Jipangu | 10.38.7.131 | 255.255.255.248 |  |
| C | WATER7 | 10.38.0.1 | 255.255.252.0 | /22 |
| C | Cipher | 10.38.0.2 | 255.255.252.0 |  |
| D | FOOSHA | 10.38.7.145 | 255.255.255.252 | /30 |
| D | WATER7 | 10.38.7.146 | 255.255.255.252 |  |
| E | FOOSHA | 10.38.7.149 | 255.255.255.252 | /30 |
| E | GUANHAO | 10.38.7.150 | 255.255.255.252 |  |
| F | GUANHAO | 10.38.6.1 | 255.255.255.0 | /24 |
| F | Elena | 10.38.6.2 | 255.255.255.0 |  |
| G | GUANHAO | 10.38.7.137 | 255.255.255.248 | /29 |
| G | Jorge | 10.38.7.138 | 255.255.255.248 |  |
| G | Maingaete | 10.38.7.139 | 255.255.255.248 |  |
| H | GUANHAO | 10.38.4.1 | 255.255.254.0 | /23 |
| H | Fukurou | 10.38.4.2 | 255.255.254.0 |  |

![143670070-31d86437-7ca2-4b4d-bf9e-29a86d5d79cb](https://user-images.githubusercontent.com/61174498/144738309-3db9fcf5-5aa3-4d9e-9c24-b40f1885a39a.png)

### CONFIG NODE

#### FOOSHA
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 5e:0d:2e:c6:9b:9a

auto eth1
iface eth1 inet static
	address 10.38.7.145
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.38.7.149
	netmask 255.255.255.252
```

#### WATER7
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.38.7.146
	netmask 255.255.255.252
  	gateway 10.38.7.145
  
auto eth1
iface eth1 inet static
	address 10.38.7.1
	netmask 255.255.255.128
  
auto eth2
iface eth2 inet static
  address 10.38.7.129
  netmask 255.255.255.248


auto eth3
iface eth3 inet static
  address 10.38.0.1
  netmask 255.255.252.0
```

#### GUANHAO
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.38.7.150
	netmask 255.255.255.252
  	gateway 10.38.7.149
  
auto eth1
iface eth1 inet static
	address 10.38.6.1
	netmask 255.255.255.0
  
auto eth2
iface eth2 inet static
  address 10.38.7.137
  netmask 255.255.255.248


auto eth3
iface eth3 inet static
  address 10.38.4.1
  netmask 255.255.254.0
```

#### Blueno
```
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.38.7.2
	netmask 255.255.255.128
	gateway 10.38.7.1
```

#### Doriki
```
auto eth0
iface eth0 inet static
	address 10.38.7.130
	netmask 255.255.255.248
	gateway 10.38.7.129	
```

#### Jipangu
```
auto eth0
iface eth0 inet static
	address 10.38.7.131
	netmask 255.255.255.248
	gateway 10.38.7.129
```

#### Cipher
```
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.38.0.2
	netmask 255.255.252.0
	gateway 10.38.0.1
```

#### Fukurou
```
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.38.4.2
	netmask 255.255.254.0
	gateway 10.38.4.1
```

#### Maingate
```
auto eth0
iface eth0 inet static
	address 10.38.7.139
	netmask 255.255.255.248
	gateway 10.38.7.137
```

#### Jorge
```
auto eth0
iface eth0 inet static
	address 10.38.7.138
	netmask 255.255.255.248
	gateway 10.38.7.137
```

#### Elena
```
auto eth0
iface eth0 inet static
#auto eth0
#iface eth0 inet dhcp
	address 10.38.6.2
	netmask 255.255.255.0
	gateway 10.38.6.2
```

## C. Setelah melakukan subnetting, Kalian juga diharuskan melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung.

### Routing

#### FOOSHA
```
# !/bin/sh

route add -net 10.38.7.0 netmask 255.255.255.128 gw 10.38.7.146
route add -net 10.38.7.128 netmask 255.255.255.248 gw 10.38.7.146
route add -net 10.38.0.0 netmask 255.255.252.0 gw 10.38.7.146

route add -net 10.38.6.0 netmask 255.255.255.0 gw 10.38.7.150
route add -net 10.38.7.136 netmask 255.255.255.248 gw 10.38.7.150
route add -net 10.38.4.0 netmask 255.255.254.0 gw 10.38.7.150
```

#### WATER7
```
# !/bin/sh

route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.38.7.145
```

#### GUANHAO
```
# !/bin/sh

route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.38.7.149
```

#### nano ./.bashrc
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.38.0.0/16
/root/config.sh
echo "nameserver 10.38.122.1" > /etc/resolv.conf
```

Routing Berhasil

![Screenshot (10429)](https://user-images.githubusercontent.com/61174498/144785902-2fa10fff-9a20-4f21-baad-8244dea5510b.png)

![Screenshot (10430)](https://user-images.githubusercontent.com/61174498/144785909-d48b9a9e-bbaf-4fa2-9ed3-16e5a2222f92.png)

![Screenshot (10432)](https://user-images.githubusercontent.com/61174498/144785915-5f4d99b3-a2e3-4844-8e3e-c8c56308a889.png)

![Screenshot (10436)](https://user-images.githubusercontent.com/61174498/144785919-a8feda84-7624-4c68-9f3a-08fe13ba2b78.png)

## D. Tugas berikutnya adalah memberikan ip pada subnet Blueno, Cipher, Fukurou, dan Elena secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.

### Doriki (DNS Server)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install bind9 -y
```

### Jipangu (DHCP Server)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install isc-dhcp-server -y
```

##### nano isc-dhcp-server
```
INTERFACES="eth0"
```

#### nano dhcpd.conf
```
# Blueno
subnet 10.38.7.0 netmask 255.255.255.128 {
    range 10.38.7.2 10.38.7.126;
    option routers 10.38.7.1;
    option broadcast-address 10.38.7.127;
    option domain-name-servers 10.38.7.130;
    default-lease-time 360;
    max-lease-time 7200;
}

# Cipher
subnet 10.38.0.0 netmask 255.255.252.0	 {
    range 10.38.0.2 10.38.3.254;
    option routers 10.38.0.1;
    option broadcast-address 10.38.3.255;
    option domain-name-servers 10.38.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Fukurou
subnet 10.38.4.0 netmask 255.255.254.0 {
    range 10.38.4.2 10.38.5.254;
    option routers 10.38.4.1;
    option broadcast-address 10.38.5.255;
    option domain-name-servers 10.38.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Elena
subnet 10.38.6.0 netmask 255.255.255.0 {
    range 10.38.6.2 10.38.6.254;
    option routers 10.38.6.1;
    option broadcast-address 10.38.6.255;
    option domain-name-servers 10.38.7.130;
    default-lease-time 720;
    max-lease-time 7200;
}

# Routing dari Jipangu ke router Water7
subnet 10.38.7.128 netmask 255.255.255.248 {
        option routers 10.38.7.129;
}

# Routing dari Jipangu ke router Guanhao
subnet 10.38.7.136 netmask 255.255.255.248 {
        option routers 10.38.7.137;
}

# Routing dari Jipangu ke router Foosha
subnet 10.38.7.144 netmask 255.255.255.252 {
        option routers 10.38.7.145;
}

# Routing dari Foosha ke Guanhao
subnet 10.38.7.148 netmask 255.255.255.252 {
        option routers 10.38.7.149;
}

# Water7
#subnet 10.38.7.144 netmask 255.255.255.252 {
#        option routers 10.38.7.145;
#}

# Guanhao
#subnet 10.38.7.148 netmask 255.255.255.252 {
#        option routers 10.38.7.149;
#}

host FOOSHA {
    hardware ethernet 5e:0d:2e:c6:9b:9a;
    fixed-address 192.168.122.98;
}
```

### [Redacted] Foosha (DHCP Relay)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start

```

##### nano /etc/default/isc-dhcp-relay
```
# What servers should the DHCP relay forward requests to?
SERVERS="10.38.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```

### Water7 (DHCP Relay)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```

##### nano /etc/default/isc-dhcp-relay
```
# What servers should the DHCP relay forward requests to?
SERVERS="10.38.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```

### Guanhao (DHCP Relay)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```

##### nano /etc/default/isc-dhcp-relay
```
# What servers should the DHCP relay forward requests to?
SERVERS="10.38.7.131"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
```

### Maingate (Web Server)

##### nano config.sh
```
# !/bin/sh

apt-get update
apt-get install isc-dhcp-relay -y

service isc-dhcp-relay start
```

### Jorge (Web Server)

##### nano config.sh
```
# !/bin/sh

apt-get update
```

### Blueno (Client)

#### All

Config ditambah:
```
auto eth0
iface eth0 inet dhcp
```

##### nano config.sh
```
# !/bin/sh

```

### Cipher
```
# !/bin/sh

```

### Fukurou
```
# !/bin/sh

```

### Elena
```
# !/bin/sh

```

## 1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

nano config.sh on Foosha
```
iptables -t nat -A POSTROUTING -s 10.38.0.0/21 -o eth0 -j SNAT --to-source 192.168.122.98
```

Yang Butuh Update (Water7, Doriki, Jipangu, dan Guanhao)
```
echo nameserver 192.168.122.1 > /etc/resolv.conf
```

Test dengan ping

![Screenshot (10472)](https://user-images.githubusercontent.com/61174498/144881484-5977bce3-150b-418f-934f-bb63d9de58dd.png)

## 2. Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.

nano config.sh on Foosha
```
iptables -A FORWARD -p tcp --dport 80 -d 10.38.7.128/29 -i eth0 -j DROP
```

```
# doriki DNS
iptables -A INPUT -s 10.38.7.130 -j DROP
# subnet a2, a3, a6, a7
iptables -A INPUT -s 10.38.7.0/25 -j DROP
iptables -A INPUT -s 10.38.0.0/22 -j DROP
iptables -A INPUT -s 10.38.4.0/23 -j DROP
iptables -A INPUT -s 10.38.6.0/24 -j DROP
```

```
iptables -A INPUT -p tcp --dport 80 -j DROP
```

Test
```
nmap 10.38.7.131
```

![Screenshot (10474)](https://user-images.githubusercontent.com/61174498/144881591-e41f907b-b39b-4e58-bc1d-dfd6fc43a3d0.png)


## 3. Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

nano config.sh on Jipangu and Doriki
```
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

![Screenshot (10475)](https://user-images.githubusercontent.com/61174498/144881765-508d6279-c7e6-4e37-b840-db83df170c4d.png)

![Screenshot (10476)](https://user-images.githubusercontent.com/61174498/144881780-6abbbb49-9ff7-464c-ac2e-4a915e6069e4.png)

![Screenshot (10477)](https://user-images.githubusercontent.com/61174498/144881810-09f5812d-eeaf-4350-b3f3-a3981aea7651.png)

![Screenshot (10478)](https://user-images.githubusercontent.com/61174498/144881826-16417fb8-bca1-443f-a502-eb0f7d2058c9.png)


Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut

## 4. Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis

Doriki
```
iptables -A INPUT -s 10.38.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 10.38.7.0/25 -m time --timestart 15:01 --timestop 23:59 -j REJECT
iptables -A INPUT -s 10.38.7.0/25 -m time --timestart 00:00 --timestop 06:59 -j REJECT
iptables -A INPUT -s 10.38.7.0/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Fri,Sat,Sun -j REJECT

iptables -A INPUT -s 10.38.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 10.38.0.0/22 -m time --timestart 15:01 --timestop 06:59 -j REJECT
iptables -A INPUT -s 10.38.0.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Fri,Sat,Sun -j REJECT
```

```
date
```

```
Senin
date -s "6 DEC 2021 08:00:00" -> bisa
date -s "6 DEC 2021 18:00:00" -> gabisa


Sabtu
date -s "13 NOV 2021 09:00:00" -> gabisa
date -s "13 NOV 2021 01:00:00" -> gabisa
```

![Screenshot (10485)](https://user-images.githubusercontent.com/61174498/144872985-e824fd2b-f6b2-4763-953f-b90f938b75e8.png)


## 5. Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

```
iptables -A INPUT -s 10.38.6.0/24 -m time --timestart 15:01 --timestop 06:59 -j REJECT

iptables -A INPUT -s 10.38.4.0/23 -m time --timestart 15:01 --timestop 06:59 -j REJECT
```

![Screenshot (10485)](https://user-images.githubusercontent.com/61174498/144882027-4fb9b445-4b3f-4641-9c76-55f8d2ae1668.png)


Selain itu di reject

## 6. Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate

```
iptables -t nat -A PREROUTING -p tcp -d 10.38.7.130 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.38.7.138:80
iptables -t nat -A PREROUTING -p tcp -d 10.38.7.130 -j DNAT --to-destination 10.38.7.139:80
iptables -t nat -A POSTROUTING -p tcp -d 10.38.7.138 --dport 80 -j SNAT --to-source 10.38.7.130
iptables -t nat -A POSTROUTING -p tcp -d 10.38.7.139 --dport 80 -j SNAT --to-source 10.38.7.130
```

Luffy berterima kasih pada kalian karena telah membantunya. Luffy juga mengingatkan agar semua aturan iptables harus disimpan pada sistem atau paling tidak kalian menyediakan script sebagai backup


### Config Penting

```
chmod +x config.sh

Water7 & Guanhao
service isc-dhcp-relay stop
service isc-dhcp-relay start

Doriki
service bind9 restart
service bind9 stop

Jipangu
service isc-dhcp-server start
service isc-dhcp-server restart
service isc-dhcp-server status
dhcpd --version

Maingate 
service squid restart
service squid status
touch /etc/squid/passwd


Client
export http_proxy=http://10.38.2.3:5000
env | grep -i proxy
unset http_proxy

ps aux | grep ping
kill -9 [pid]
```

Problem:
1.)
