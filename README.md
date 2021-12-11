# Jarkom-Modul-5-A15-2021

Laporan Resmi Modul 5 Jaringan Komputer Kelompok A15

## Anggota Kelompok :

|      NRP       |     Nama     |
| :------------: | :----------: |
| 05111940000034 | Aimar Wibowo |
| 05111940000064 | Ifanu Antoni |

&nbsp;

## Topologi

## Subnetting (VLSM)

### Pembagian Subnet

|      Subnet       |     Jumlah IP     |     Netmask     |
|  :--------------: | :--------------:  | :--------------:|
|A1|2|/30|
|A2|2|/30|
|A3|201|/24|
|A4|301|/23|
|A5|101|/25|
|A6|701|/22|
|A7|4|/29|
|A8|4|/29|
|**Total**|**1316**|**/21**|

### VLSM Tree

### Pembagian IP

|      Subnet       |     Network ID    |     Netmask     |
|  :--------------: | :--------------:  | :--------------:|
|A1|192.176.0.0|255.255.255.252|
|A2|192.176.0.4|255.255.255.252|
|A3|192.176.1.0|255.255.255.0|
|A4|192.176.2.0|255.255.254.0|
|A5|192.176.0.128|255.255.255.128|
|A6|192.176.4.0|255.255.252.0|
|A7|192.176.0.16|255.255.255.248|
|A8|192.176.0.24|255.255.255.248|

## Setting GNS3

**FOOSHA (sebagai Router / DHCP Relay)**

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.176.0.1
        netmask 255.255.255.252

auto eth2
iface eth2 inet static
         address 192.176.0.5
         netmask 255.255.255.252
```

**WATER7 (sebagai Router / DHCP Relay)**

```
auto eth0
iface eth0 inet static
        address 192.176.0.2
        netmask 255.255.255.252
        gateway 192.176.0.1

auto eth1
iface eth1 inet static
        address 192.176.0.17
        netmask 255.255.255.248

auto eth2
iface eth2 inet static
         address 192.176.0.129
         netmask 255.255.255.128

auto eth3
iface eth3 inet static
         address 192.176.4.1
         netmask 255.255.252.0
```

**GUANHAO (sebagai Router / DHCP Relay)**

```
auto eth0
iface eth0 inet static
          address 192.176.0.6
          netmask 255.255.255.252
          gateway 192.176.0.5

auto eth1
iface eth1 inet static
          address 192.176.0.25
          netmask 255.255.255.248

auto eth2
iface eth2 inet static
          address 192.176.2.1
          netmask 255.255.254.0

auto eth3
iface eth3 inet static
          address 192.176.1.1
          netmask 255.255.255.0
```

**DORIKI (sebagai DNS Server)**

```
auto eth0
iface eth0 inet static
       address 192.176.0.18
       netmask 255.255.255.248
       gateway 192.176.0.17
```

**JIPANGU (sebagai DHCP Server)**

```
auto eth0
iface eth0 inet static
       address 192.176.0.19
       netmask 255.255.255.248
       gateway 192.176.0.17
```

**JORGE (sebagai Web Server)**

```
auto eth0
iface eth0 inet static
       address 192.176.0.26
       netmask 255.255.255.248
       gateway 192.176.0.25
```

**MAINGATE (sebagai Web Server)**

```
auto eth0
iface eth0 inet static
       address 192.176.0.27
       netmask 255.255.255.248
       gateway 192.176.0.25
```

**BLUENO (sebagai Client)**

```
auto eth0
iface eth0 inet dhcp
```

**CIPHER (sebagai Client)**

```
auto eth0
iface eth0 inet dhcp
```

**ELENA (sebagai Client)**

```
auto eth0
iface eth0 inet dhcp
```

**FUKUROU (sebagai Client)**

```
auto eth0
iface eth0 inet dhcp
```

## Routing

**Foosha**

```
route add -net 192.176.0.16 netmask 255.255.255.248 gw 192.176.0.2
route add -net 192.176.0.128 netmask 255.255.255.128 gw 192.176.0.2
route add -net 192.176.4.0 netmask 255.255.252.0 gw 192.176.0.2
route add -net 192.176.0.24 netmask 255.255.255.248 gw 192.176.0.6
route add -net 192.176.2.0 netmask 255.255.254.0 gw 192.176.0.6
route add -net 192.176.1.0 netmask 255.255.255.0 gw 192.176.0.6
```

## Setting DHCP Relay

**Pada Foosha, WATER7, dan GUANHAO**
1. Install aplikasi isc-dhcp-relay.
```
apt-get install isc-dhcp-relay -y
```
2. Edit file `/etc/default/isc-dhcp-relay` seperti pada gambar berikut :
3. Restart isc-dhcp-relay.
```
service isc-dhcp-relay restart
```

## Setting DHCP Server

**Pada JIPANGU**

1. Install aplikasi isc-dhcp-server.
```
apt-get install isc-dhcp-server -y
```
2. Edit file `/etc/default/isc-dhcp-server` seperti pada gambar berikut :
3. Edit file `/etc/dhcp/dhcpd.conf` untuk menambahkan subnet sebagai berikut :
4. Restart isc-dhcp-server.
```
service isc-dhcp-server restart
```

## Setting DNS Server

**Pada DORIKI**

1. Install aplikasi bind9.
```
apt-get install bind9 -y
```

2. Edit file `/etc/bind/named.conf.options` seperti pada gambar berikut :
3. Restart bind9.
```
service bind9 restart
```

&nbsp;

## No 1

Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

### Jawaban

## No 2

Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang merupakan DHCP Server dan DNS Server demi menjaga keamanan.

### Jawaban

## No 3

Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

### Jawaban

## No 4

Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

### Jawaban

## No 5

Akses dari subnet Elena dan Fukurou hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

### Jawaban

## No 6

Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate.

### Jawaban

&nbsp;

## Kendala 

1.
