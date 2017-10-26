# Tugas 1 - Uji Penetrasi

## Pendahuluan

## Dasar Teori

### Ubuntu Server
Ubuntu Server adalah sistem operasi turunan dari Linux Ubuntu yang di desain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Pada Ubuntu Server tidak terdapat GUI dan hanya menggunakan CLI (Command Line Interface). Ubuntu Server menyediakan platform yang dapat memudahkan proses deploy server dengan fasilitas layanan internet standar, seperti mail, web, DNS, file-serving, hingga manajemen database. Ubuntu Server tidak membiarkan keberadaan port terbuka setelah proses instalasi, dan hanya akan memuat software yang dibutuhkan untuk membangun sebuah sistem server yang aman.

### Ubuntu Desktop
Ubuntu merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai software bebas. Ubuntu Desktop ditujukan untuk user yang memakai Ubuntu sebagai end user. Pada Ubuntu Desktop telahterinstall beberapa aplikasi, diantaranya: LibreOffice, Mozilla Firefox, dan Mozilla Thunderbird. Ubuntu Desktop mengompile paket menggunakan fitur gcc seperti PIE dan proteksi Buffer Overflow untuk memproteksi software.

### OpenSSH Server
OpenSSH adalah satu set aplikasi komputer yang bisa mendukung sesi komunikasi terenkripsi pada jaringan komputer menggunakan protokol ssh. Awalnya aplikasi ini dikembangkan sebagai aplikasi open source yang menjadi alternatif dari aplikasi serupa yang berbayar. OpenSSH dikembangkan dan merupakan bagian dari proyek OpenBSD. Dalam perkembangan selanjutnya, OpenSSH tidak hanya memberikan aplikasi remote shell melalui ssh atau remote eksekusi program saja, tapi bisa digunakan untuk tunnelling atau setup vpn antara dua jaringan.

### THC-Hydra
THC-Hydra adalah login cracker paralel yang mendukung penyerangan terhadap berbagai macam protokol. THC-Hydra sangat cepat dan fleksibel, dan mudah untuk menambahkan modul-modul baru. Alat ini memungkinkan para periset dan konsultan keamanan untuk menunjukkan betapa mudahnya mendapatkan akses yang tidak sah ke sistem jarak jauh.
THC-Hydra mendukung: Cisco AAA, Cisco auth, Cisco enable, CVS, FTP, HTTP(S)-FORM-GET, HTTP(S)-FORM-POST, HTTP(S)-GET, HTTP(S)-HEAD, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MySQL, NNTP, Oracle Listener, Oracle SID, PC-Anywhere, PC-NFS, POP3, PostgreSQL, RDP, Rexec, Rlogin, Rsh, SIP, SMB(NT), SMTP, SMTP Enum, SNMP v1+v2+v3, SOCKS5, SSH (v1 and v2), SSHKEY, Subversion, Teamspeak (TS2), Telnet, VMware-Auth, VNC and XMPP.

### Ncrack
Ncrack adalah alat cracking otentikasi jaringan berkecepatan tinggi. Ini dibangun untuk membantu perusahaan mengamankan jaringan mereka dengan secara proaktif menguji semua host dan perangkat jaringan mereka dengan kata kunci yang buruk. Profesional keamanan juga mengandalkan Ncrack saat mengaudit klien mereka. Ncrack dirancang menggunakan pendekatan modular, sintaks baris perintah yang mirip dengan Nmap dan mesin dinamis yang dapat menyesuaikan perilakunya berdasarkan umpan balik jaringan. Ini memungkinkan dilakukannya audit berskala besar yang cepat namun dapat diandalkan dari beberapa host.

Fitur Ncrack mencakup antarmuka yang sangat fleksibel yang memberi pengguna kontrol penuh atas operasi jaringan, memungkinkan serangan bruteforcing yang sangat canggih, template waktu untuk kemudahan penggunaan, interaksi runtime yang mirip dengan Nmap dan banyak lagi. Protokol yang didukung meliputi RDP, SSH, HTTP (S), SMB, POP3 (S), VNC, FTP, SIP, Redis, PostgreSQL, MySQL, dan Telnet.

Ncrack dilepaskan sebagai alat standalone dan bisa diunduh dari bagian di bawah ini. Pastikan untuk membaca halaman manual Ncrack untuk memahami penggunaan Ncrack. Jika Anda seorang pengembang dan ingin menulis modul Ncrack Anda sendiri, pelajari Panduan Pengembang Ncrack akan menjadi langkah pertama.

### Medusa

### Fail2Ban

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

- Ketik 'Y' dan tekan untuk melanjutkan instalasi:

![ketik Y](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bssh%5D02.PNG)

- Instalasi OpenSSH Server akan kembali berjalan hingga selesai. Untuk memastikan OpenSSH Server telah terinstal dengan baik, masukkan perintah berikut pada terminal:

<pre>
service ssh status
</pre>

![hasil dari perintah service ssh status](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bssh%5D04.PNG)

### 4. Langkah Uji Penetrasi dengah SSH Brute Force Tools

## Uji Penetrasi 2

### 1. Langkah Konfigurasi Fail2ban

### 2. Langkah Konfigurasi SSH Server

### 3. Langkah Uji Penetrasi dengah SSH Brute Force Tools

## Kesimpulan dan Saran

