# Jarkom-Modul-3-B07-2023
> Laporan Resmi Praktikum 3 Jaringan Komputer B07
***
## Anggota Kelompok B07
1. I Gusti Ngurah Ervan Juli Ardana (5025211295)
2. Danar Sodik Priyambodo (5025211145)

## Daftar isi
+ [TOPOLOGI](#topologi)
+ [SOAL 1](#soal-1)
+ [SOAL 2](#soal-2)
+ [SOAL 3](#soal-3)
+ [SOAL 4](#soal-4)
+ [SOAL 5](#soal-5)
+ [SOAL 6](#soal-6)
+ [SOAL 7](#soal-7)
+ [SOAL 8](#soal-8)
+ [SOAL 9](#soal-9)
+ [SOAL 10](#soal-10)
+ [SOAL 11](#soal-11)
+ [SOAL 12](#soal-12)
+ [SOAL 13](#soal-13)
+ [SOAL 14](#soal-14)
+ [SOAL 15](#soal-15)
+ [SOAL 16](#soal-16)
+ [SOAL 17](#soal-17)
+ [SOAL 18](#soal-18)
+ [SOAL 19](#soal-19)
+ [SOAL 20](#soal-20)

---
## TOPOLOGI
<img width="938" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/78541993-aedf-4063-8d5f-e3fbf5b3bb51">

---
## SOAL 0
### Pertanyaan
melakukan register domain berupa riegel.canyon.yyy.com untuk worker Laravel dan granz.channel.yyy.com untuk worker PHP (0) mengarah pada worker yang memiliki IP [prefix IP].x.1.
### Solusi
pada soal 0 kita diminta untuk membuat domain untuk  worker laravel berupa riegel.canyon.B07.com dan worker PHP berupa granz.channel.B07.com dan mengarah pada worker yang memiliki IP [prefix IP].x.1. Caranya yaitu kita perlu menjalankan perintah dibawah yang terdapat dalam Script.sh yang kami miliki

```
echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt-get install bind9 -y

echo '
zone "riegel.canyon.b07.com" {
        type master;
        file "/etc/bind/jarkom/riegel.canyon.b07.com";
};

zone "granz.channel.b07.com" {
        type master;
        file "/etc/bind/jarkom/granz.channel.b07.com";
};' > /etc/bind/named.conf.local

mkdir /etc/bind/jarkom
cp /etc/bind/db.local /etc/bind/jarkom/riegel.canyon.b07.com
cp /etc/bind/db.local /etc/bind/jarkom/granz.channel.b17.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     riegel.canyon.b07.com. root.riegel.canyon.b07.com. (
                     2023111301         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      riegel.canyon.b07.com.
@       IN      A       10.12.4.1       ; IP Flieren
@       IN      AAAA    ::1
' > /etc/bind/jarkom/riegel.canyon.b07.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     granz.channel.b07.com. root.granz.channel.b07.com. (
                     2023111302         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      granz.channel.b07.com.
@       IN      A       10.12.3.1       ; IP Lawine
@       IN      AAAA    ::1

' > /etc/bind/jarkom/granz.channel.b07.com

service bind9 restart
```
##Testing
Selanjutnya kita bisa melakukan test apakah domain tersebut sudah berjalan atau belum dengan cara melakukan ping kepada client tersebut melalui client

<img width="359" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/9cef7a44-736f-4c74-8086-c688a5609bda">
<img width="367" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/040e821d-51d9-4d2c-b7c1-379d3b9b6688">


---
## SOAL 1
### Pertanyaan
Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.
### Solusi
## Aura
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.12.1.0
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.12.2.0
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 10.12.3.0
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 10.12.4.0
	netmask 255.255.255.0
```

## Himmel
```
auto eth0
iface eth0 inet static
	address 10.12.1.1
	netmask 255.255.255.0
	gateway 10.12.1.0
```
## Heiter
```
auto eth0
iface eth0 inet static
	address 10.12.1.2
	netmask 255.255.255.0
	gateway 10.12.1.0
```
## Denken
```
auto eth0
iface eth0 inet static
	address 10.12.2.1
	netmask 255.255.255.0
	gateway 10.12.2.0
```
## Eisen
```
auto eth0
iface eth0 inet static
	address 10.12.2.2
	netmask 255.255.255.0
	gateway 10.12.2.0
```
## Lawine
```
auto eth0
iface eth0 inet static
	address 10.12.3.1
	netmask 255.255.255.0
	gateway 10.12.3.0
```
## Linie
```
auto eth0
iface eth0 inet static
	address 10.12.3.2
	netmask 255.255.255.0
	gateway 10.12.3.0
```
## Lugner
```
auto eth0
iface eth0 inet static
	address 10.12.3.3
	netmask 255.255.255.0
	gateway 10.12.3.0
```
## Frieren
```
auto eth0
iface eth0 inet static
	address 10.12.4.1
	netmask 255.255.255.0
	gateway 10.12.4.0
```
## Flamme
```
auto eth0
iface eth0 inet static
	address 10.12.4.2
	netmask 255.255.255.0
	gateway 10.12.4.0
```
## Fern
```
auto eth0
iface eth0 inet static
	address 10.12.4.3
	netmask 255.255.255.0
	gateway 10.12.4.0
```
## Semua Client (Sein, Stark, Revolte, Richter)
```
auto eth0
iface eth0 inet dhcp
```
---
## SOAL 2
### Pertanyaan
Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80 
### Solusi
Pada soal kedua kita diminta untuk semua Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80. Caranya yaitu kita perlu menjalankan perintah pada Script.sh yang sudah kita miliki seperti dibawah ini
```
echo '
subnet 10.12.1.0 netmask 255.255.255.0 {
}

subnet 10.12.2.0 netmask 255.255.255.0 {
}

subnet 10.12.3.0 netmask 255.255.255.0 {
    range 10.12.3.16 10.12.3.32;
    range 10.12.3.64 10.12.3.80;
    option routers 10.12.3.0;
} > /etc/dhcp/dhcpd.conf
```

---
## SOAL 3
### Pertanyaan
Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168
### Solusi
pada soal ketiga kita diminta untuk semua Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168. caranya kita hanya perlu menambahkan sedikit script.sh yang kita miliki
```
echo '
subnet 10.12.1.0 netmask 255.255.255.0 {
}

subnet 10.12.2.0 netmask 255.255.255.0 {
}

subnet 10.12.3.0 netmask 255.255.255.0 {
    range 10.12.3.16 10.12.3.32;
    range 10.12.3.64 10.12.3.80;
    option routers 10.12.3.0;
}
subnet 10.12.4.0 netmask 255.255.255.0 {
    range 10.12.4.12 10.12.4.20;
    range 10.12.4.160 10.12.4.168;
    option routers 10.12.4.0;
}' > /etc/dhcp/dhcpd.conf
```
---
## SOAL 4
### Pertanyaan
Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut
### Solusi
pada pertanyaan 4 kita diminta agar Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut. Caranya yaitu kita hanya perlu melengkapi sedikit konfigurasi dari no 2 dan 3 pada script.sh kita berupa
```
echo '
subnet 10.12.1.0 netmask 255.255.255.0 {
}

subnet 10.12.2.0 netmask 255.255.255.0 {
}

subnet 10.12.3.0 netmask 255.255.255.0 {
    range 10.12.3.16 10.12.3.32;
    range 10.12.3.64 10.12.3.80;
    option routers 10.12.3.0;
    option broadcast-address 10.12.3.255;
    option domain-name-servers 10.12.1.2;
    default-lease-time 180;
    max-lease-time 5760;
}

subnet 10.12.4.0 netmask 255.255.255.0 {
    range 10.12.4.12 10.12.4.20;
    range 10.12.4.160 10.12.4.168;
    option routers 10.12.4.0;
    option broadcast-address 10.12.4.255;
    option domain-name-servers 10.12.1.2;
    default-lease-time 720;
    max-lease-time 5760;
}' /etc/dhcp/dhcpd.conf
```
Kemudian agar client dapat terhubung kepada internet kita perlu melakukan DNS Forwarder dari Heiter. Caranya yaitu pada `/etc/bind/named.conf.options` Uncomment pada bagian dibawah ini
```
forwarders {
    192.168.122.1;
};
```
Kemudian comment bagian ini
```
// dnssec-validation auto;
```
Terakhir tambahkan 
```
allow-query{any;};
```
setelah melakukan semuanya kita hanya perlu melakukan restart pada bind9 lalu bisa mencoba melakukan ping pada client

## Testing
<img width="330" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/3c0bf475-5878-4785-859e-c1c179ad2b60">
<img width="360" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/0eecb172-6ac2-4924-83de-032a6681b22d">

---
## SOAL 5
### Pertanyaan
Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit
### Solusi
pada soal 5 kita diminta untuk mengatur lease time dari masing masing switch. Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Caranya yaitu kita hanya perlu menambahkan `default-lease-time` dan `max-lease-team` pada konfigurasi masing masing switch seperti dibawah ini
```
subnet 10.12.3.0 netmask 255.255.255.0 {
    range 10.12.3.16 10.12.3.32;
    range 10.12.3.64 10.12.3.80;
    option routers 10.12.3.0;
    option broadcast-address 10.12.3.255;
    option domain-name-servers 10.12.1.2;
    default-lease-time 180;
    max-lease-time 5760;
}

subnet 10.12.4.0 netmask 255.255.255.0 {
    range 10.12.4.12 10.12.4.20;
    range 10.12.4.160 10.12.4.168;
    option routers 10.12.4.0;
    option broadcast-address 10.12.4.255;
    option domain-name-servers 10.12.1.2;
    default-lease-time 720;
    max-lease-time 5760;
}
```
Setelah mengatur lease time dari masing masing switch kita bisa melakukan testing pada salah satu client dari masing masing switch
## Testing
<img width="385" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/05b6fff6-dc3e-4d8c-a6ac-fca7395056fb">
<img width="361" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/bde16d55-4c83-4867-a227-fb248403713e">

---
## SOAL 6
### Pertanyaan

### Solusi

---
## SOAL 7
### Pertanyaan

### Solusi

---
## SOAL 8
### Pertanyaan

### Solusi

---
## SOAL 9
### Pertanyaan

### Solusi

---
## SOAL 10
### Pertanyaan

### Solusi

---
## SOAL 11
### Pertanyaan

### Solusi

---
## SOAL 12
### Pertanyaan

### Solusi

---
## SOAL 13
### Pertanyaan

### Solusi

---
## SOAL 14
### Pertanyaan

### Solusi

---
## SOAL 15
### Pertanyaan

### Solusi

---
## SOAL 16
### Pertanyaan

### Solusi

---
## SOAL 17
### Pertanyaan

### Solusi

---
## SOAL 18
### Pertanyaan

### Solusi

---
## SOAL 19
### Pertanyaan

### Solusi

---
## SOAL 20
### Pertanyaan

### Solusi
