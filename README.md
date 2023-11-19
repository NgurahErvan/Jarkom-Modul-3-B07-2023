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
Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3
### Solusi
Pertama tama kita perlu melakukan download konfigurasi yang telah diberikan menggunakan wget 
```
wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=1ViSkRq7SmwZgdK64eRbr5Fm1EGCTPrU1' -O granz.channel.b07.com.zip 
unzip -o /var/www/granz.channel.b07.com -d /var/www/
```
Kemudian Pada masing-masing worker PHP, lakukan konfigurasi virtual host berikut seperti dibawah ini
```
apt-get update
apt install nginx php php-fpm -y
apt-get install wget -y
apt-get install unzip -y
apt-get install htop -y
apt-get install lynx -y
service php7.3-fpm start
php -v
service nginx start
mkdir /var/www/jarkom
cp -v -r /root/modul-3/* /var/www/jarkom/
touch /etc/nginx/sites-available/jarkom

echo '
server {

        listen 80;

        root /var/www/jarkom;

        index index.php index.html index.htm;
        server_name 10.12.3.1;

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
    }

    location ~ /\.ht {
                        deny all;
        }

        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log;
}' > /etc/nginx/sites-available/jarkom

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service php7.3-fpm restart
service nginx restart
```
## Testing
Kita dapat melakukan testing dengan melakukan `lynx localhost`

<img width="949" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/8790f843-ce5e-4816-9cde-ef1b23f36ab6">

---
## SOAL 7
### Pertanyaan
Kepala suku dari Bredt Region memberikan resource server sebagai berikut:
Lawine, 4GB, 2vCPU, dan 80 GB SSD.
Linie, 2GB, 2vCPU, dan 50 GB SSD.
Lugner 1GB, 1vCPU, dan 25 GB SSD.
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second
### Solusi
Pertama tama kita perlu mengarahkan kembali kedua domain tersebut menuju ip Load Balancer (Eisen) pada DNS Server (Heiter)
```
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
@       IN      A       10.12.2.2       ; IP Eisen
@       IN      AAAA    ::1

' > /etc/bind/jarkom/granz.channel.b07.com

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
@       IN      A       10.12.2.2       ; IP Eisen
@       IN      AAAA    ::1

' > /etc/bind/jarkom/riegel.canyon.b07.com

service bind9 restart
```
Setelah itu pada load balancer kita perlu menambahkan sedikit konfigurasi
```
echo '
# Default menggunakan Round Robin
upstream myweb  {
    server 10.12.3.1; #IP Lawine
    server 10.12.3.2; #IP Linie
    server 10.12.3.3; #IP Lugnar
}

server {
    listen 80;
    server_name granz.channel.b07.com;

    location / {
    proxy_pass http://myweb;
    }
}' > /etc/nginx/sites-available/lb-jarkom-php

service nginx restart
```
## Testing
setelah itu kita bisa melakukan testing dari salah satu client menggunakan
```
ab -n 1000 -c 100 granz.channel.b07.com/ 
```

<img width="454" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/b7936f97-ede4-4561-8b13-f62471825eca">
---
## SOAL 8
### Pertanyaan
Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:
Nama Algoritma Load Balancer
Report hasil testing pada Apache Benchmark
Grafik request per second untuk masing masing algoritma. 
Analisis (8)
### Solusi
caranya kita hanya perlu menjalankan 
```
ab -n 200 -c 10 granz.channel.b07.com/ 
```
#Testing
## Round Robin
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/37164c55-a82d-41a1-a409-6bd57822cfd4)

## Least-connection
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/3d4deef5-56b4-4107-822b-5aad0bce590b)

## IP Hash
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/b06cd881-cc35-441c-ab98-575877747758)

## Generic Hash
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/b3e46795-1ff8-427d-a623-d08c5ec40c84)

## Grafik
<img width="461" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/6277edcc-fd5e-4327-9afe-7dd4d76dcb07">

## Analisis
Berdasarkan data yang disediakan, empat algoritma penjadwalan—Round Robin, Least Connection, IP Hash, dan Generic Hash—telah dibandingkan dalam konteks pengujian dengan perintah ab -n 200 -c 10 granz.channel.b07.com/. Dalam hal kinerja request per second (RPS), Least Connection, IP Hash, dan Generic Hash menunjukkan hasil yang lebih tinggi dibandingkan Round Robin. Least Connection mencapai 680 RPS, sementara IP Hash dan Generic Hash masing-masing mencapai 707 RPS dan 716 RPS.

Penggunaan CPU pada masing-masing worker juga memberikan wawasan penting. Round Robin menunjukkan distribusi yang merata pada ketiga worker-nya. Least Connection memiliki sedikit lonjakan penggunaan CPU pada Worker Lugner dan Worker Linie, mungkin mencerminkan beban koneksi yang lebih tinggi pada server-server tersebut. IP Hash menunjukkan distribusi penggunaan CPU yang merata, sesuai dengan distribusi beban kerja berdasarkan alamat IP. Sementara Generic Hash, meskipun memberikan hasil RPS tertinggi, menunjukkan lonjakan penggunaan CPU pada Worker Lugner.

Dengan demikian, pemilihan algoritma tergantung pada kebutuhan dan karakteristik lingkungan. Round Robin dan Least Connection cocok untuk situasi dengan beban kerja merata atau ketika beban koneksi memainkan peran kunci. IP Hash dapat diandalkan untuk distribusi beban kerja berdasarkan alamat IP, sementara Generic Hash menonjol dalam hal RPS, meskipun perlu memperhatikan penggunaan CPU yang lebih tinggi pada salah satu worker.

---
## SOAL 9
### Pertanyaan
Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire.
### Solusi
Kita hanya perlu melakukan testing menggunakan 
```
ab -n 100 -c 10 granz.channel.b07.com
```
## 3 Worker
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/8e33f518-5a60-4f21-b618-ab568896ba9f)

## 2 Worker
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/7f36efb8-5f24-4ebb-8701-68ef0e55ef1d)

## 1 Worker
![image](https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/a9f180b2-91f6-498a-b5d8-166bb7f9cd4f)

## Grafik
<img width="455" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/2fcdbab5-4baf-4bfa-9af9-070e81d26caf">

---
## SOAL 10
### Pertanyaan
Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/
### Solusi
Pertama tama kita perlu membuat folder rahasiakita
```
mkdir /etc/nginx/rahasisakita
echo 'ajkb07' | htpasswd -ic /etc/nginx/rahasisakita/.htpasswd netics
```
Kemudian tambahkan sedikit konfigurasi pada load balancer yang mengatur autentikasi
```
auth_basic "Administrator'\''s Area";
auth_basic_user_file /etc/nginx/rahasiakita/.htpasswd;
```
## Testing
untuk melakukan testing kita hanya perlu mengakses kembali domain
```
lynx granz.channel.b07.com
```
<img width="940" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/162120ca-cfb4-4d4b-b78d-d0190be41461">

<img width="706" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/b8ba8e51-c15a-4603-936d-241638ed5805">

<img width="903" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/c7c9de33-7086-4cc0-ad23-7f3a53a69f7d">

<img width="936" alt="image" src="https://github.com/NgurahErvan/Jarkom-Modul-3-B07-2023-/assets/114007640/bc04cb7e-f46f-471a-8165-f4fc3aa8084a">


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
