# Tugas 1 - Uji Penetrasi

## Pendahuluan

## Dasar Teori

### Ubuntu Server
Ubuntu Server adalah sistem operasi turunan dari Linux Ubuntu yang di desain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Pada Ubuntu Server tidak terdapat GUI dan hanya menggunakan CLI (Command Line Interface). Ubuntu Server menyediakan platform yang dapat memudahkan proses deploy server dengan fasilitas layanan internet standar, seperti mail, web, DNS, file-serving, hingga manajemen database. Ubuntu Server tidak membiarkan keberadaan port terbuka setelah proses instalasi, dan hanya akan memuat software yang dibutuhkan untuk membangun sebuah sistem server yang aman.

### Ubuntu Desktop
Ubuntu merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai software bebas. Ubuntu Desktop ditujukan untuk user yang memakai Ubuntu sebagai end user. Pada Ubuntu Desktop telahterinstall beberapa aplikasi, diantaranya: LibreOffice, Mozilla Firefox, dan Mozilla Thunderbird. Ubuntu Desktop mengompile paket menggunakan fitur gcc seperti PIE dan proteksi Buffer Overflow untuk memproteksi software.

### SSH Server
Fungsi SSH Server: Menggantikan telnet, rlogin, ftp, dan rsh, salah satu fungsi utamanya adalah untuk menjamin keamanan dalam melakukan transmisi data pada suatu jaringan. Melakukan enkripsi terhadap data yang dikirim. Protokol untuk pertukaran data dalam suatu jaringan. Otentifikasi, mekanisme untuk memastikan pengirim dan penerima adalah benar dan aman. Kerahasiaan, memastikan kerahasiaan data yang dikirim agar hanya diketahui oleh penerima dan pengirim.

### THC Hydra

### NCrack

### Medusa

### Fail2Ban

###

## Uji Penetrasi 1

### 1. Langkah Instalasi Ubuntu Server

- Pilih bahasa untuk menu installasi.

![menu pilih bahasa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/1.pilih_bahasa.PNG)

- Pilih 'Install Ubuntu Server' pada menu installasi.

![pilih install](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/2.pilih_install_ubuntu_server.PNG)

- Pilih bahasa untuk OS Ubuntu Server.

![pilih bahasa OS](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/3.pilih_bahasa_ubuntu_server.PNG)

- Pilih lokasi yang nanti akan digunakan saat menentukan timezone dan system locale.

![pilih lokasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/4.pilih_lokasi.PNG)

### 2. Langkah Instalasi Ubuntu Desktop

### 3. Langkah Instalasi SSH Server

- Masukkan perintah berikut pada terminal:

<pre>
sudo apt-get install openssh-server
</pre>

- Ketik 'Y' untuk melanjutkan instalasi:

![ketik Y](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bssh%5D02.PNG)

### 4. Langkah Uji Penetrasi dengah SSH Brute Force Tools
