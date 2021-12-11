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

## Setting DHCP Relay

## Setting DHCP Server

## Setting DNS Server

