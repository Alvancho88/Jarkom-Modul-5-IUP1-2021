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

### CONFIG NODE

### FOOSHA
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

### WATER7
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

### GUANHAO
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

### Blueno
```

```

### Doriki
```

```

### Jipangu
```

```

### Cipher
```

```

### Fukurou
```

```

### Maingate
```

```

### Jorge
```

```

### Elena
```

```


## C. Setelah melakukan subnetting, Kalian juga diharuskan melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung.

## D. Tugas berikutnya adalah memberikan ip pada subnet Blueno, Cipher, Fukurou, dan Elena secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.

## 1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

## 2. Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.

## 3. Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

## Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut

## 4. Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis

## 5. Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

## Selain itu di reject

## 6. Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate

### Luffy berterima kasih pada kalian karena telah membantunya. Luffy juga mengingatkan agar semua aturan iptables harus disimpan pada sistem atau paling tidak kalian menyediakan script sebagai backup







