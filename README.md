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
| H | GUANHAO | 10.38.4.1 | 255.255.254.0	 | /23 |
| H | Fukurou | 10.38.4.2 | 255.255.254.0	 |  |

![143670070-31d86437-7ca2-4b4d-bf9e-29a86d5d79cb](https://user-images.githubusercontent.com/61174498/144738309-3db9fcf5-5aa3-4d9e-9c24-b40f1885a39a.png)

### CONFIG NODE

#### FOOSHA
```
auto eth0
iface eth0 inet dhcp

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
subnet 10.38.7.0 netmask 255.255.255.128 {
    range 10.38.7.10 10.38.7.100;
    option routers 10.38.1.1;
    option broadcast-address 10.38.1.255;
    option domain-name-servers 10.38.2.2;
    default-lease-time 360;
    max-lease-time 7200;
}

subnet 10.38.3.0 netmask 255.255.255.0 {
    range 10.38.3.30 10.38.3.50;
    option routers 10.38.3.1;
    option broadcast-address 10.38.3.255;
    option domain-name-servers 10.38.2.2;
    default-lease-time 720;
    max-lease-time 7200;
}

subnet 10.38.2.0 netmask 255.255.255.0 {
        option routers 10.38.2.1;
}

host Skypie {
    hardware ethernet 66:f9:90:6c:ae:ae;
    fixed-address 10.38.3.69;
}
```

### Foosha (DHCP Relay)

##### nano config.sh
```
# !/bin/sh

apt-get update

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

## 2. Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.

## 3. Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

## Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut

## 4. Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis

## 5. Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

## Selain itu di reject

## 6. Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate

### Luffy berterima kasih pada kalian karena telah membantunya. Luffy juga mengingatkan agar semua aturan iptables harus disimpan pada sistem atau paling tidak kalian menyediakan script sebagai backup







