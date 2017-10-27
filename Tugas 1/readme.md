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

- Bila dari kombinasi antara bahasa OS yang dipilih dan lokasi yang dipilih tidak ditemukan locale yang tepat, maka pengguna dapat memilih locale secara manual.

![pilih locale](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/5.pilih_konfigurasi_lokal.PNG)

- Konfigurasi layout dari keyboard, pilih 'Yes' bila ingin melakukan test untuk mendapatkan layout keyboard, pilih 'No' untuk memilih layout yang disediakan.

![pilih layout keyboard](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/6.konfigurasi_keyboard.PNG)

- Bila memilih 'Yes', maka akan muncul serangkaian test untuk mencocokan character yang ditampilkan dengan yang berada pada keyboard. Kemudian dari hasil test tersebut didapatkan layout keyboard.

![hasil test keyboard](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/7.konfigurasi_keyboard2.PNG)

- Input nama yang dikendahaki untuk hostname, hostname berfungsi sebagai pengenal sistem pada jaringan.

![input hostname](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/9.konfigurasi_network.PNG)

- Input nama lengkap dari akun user yang akan dibuat untuk kegiatan non-adminitratif.

![input fullname](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/10.set-up_fullname.PNG)

- Input username untuk akun user baru. Username harus mulai dari huruf kecil dan dapat diikuti oleh kombinasi angka dan huruf kecil lainnya.

![input username](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/11.set-up_username.PNG)

- Input sandi/password untuk akun baru.

![input password](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/12.set-up_password.PNG)

- Input ulang sandi/password untuk akun baru yang telah dimasukkan dilangkah sebelumnya.

![input ulang password](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/13.re-type_password.PNG)

- Mengenkripsi direktori home, sehingga file yang tersimpan bersifat pribadi. Pilih 'Yes' untuk mengekripsi home, pilih 'No' untuk melanjutkan instalasi tanpa mengenkripsi direktori home.

![pilihan enkripsi home direktori](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/14.enkrip_direktori_home.PNG)

- Timezone telah dipilih secara otomatis dari lokasi fisik komputer yang sedang melakukan instalasi. Bila hasil pemilihan benar, pilih 'Yes' untuk melanjutkan instalasi. Bila hasil kurang sesuai, pilih 'No' untuk memilih timezone secara manual dari list.

![pengaturan timezone](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/15.setting_up_clock.PNG)

- Bila memilih 'No' pada pilihan sebelumnya, sekarang anda akan memilih manual timezone dari list yang disediakan.

![pilih timezone](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/16.setting_up_clock.PNG)

- Pilih metode partisi disk yang ingin digunakan, pilih 'Guided - user entire disk and set up LVM' bila ingin diarahkan pada saat mempartisi disk dan pengaturan Logical Volume Manager oleh sistem instalasi.

![pilih metode partisi disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/17.partition_disk.PNG)

- Pilih disk yang akan dipartisi, dimana disk yang dipilih akan dihapus datanya pada saat partisi.

![pilih disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/18.partition_disk.PNG)

- Pilih 'Yes' bila telah yakin akan disk yang akan dipartisi dan melanjutkan ke konfigurasi LVM. Pilih 'No' untuk kembali ke tahap sebelumnya untuk memilih disk.

![konfirmasi pilih disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/19.partition_disk.PNG)

- Inputkan besar ukuran dari volume group yang dikehendaki untuk partisi disk.

![input ukuran disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/20.partition_disk.PNG)

- Konfirmasi dari pilihan dari tahap sebelumnya dan informasi yang akan terjadi pada disk anda saat di write. Pilih 'Yes' untuk sistem melakukan partisi dan melanjutkan ke langkah selanjutnya. Pilih 'No' untuk kembali ke langkah sebelumnya.

![konfirmasi sebelum disk di write](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/21.partition_disk.PNG)

- Bila diperlukan proxy untuk mengakses internet, maka inputkan informasi HTTP proxy dan bila tidak maka dapat dikosongkan. Kemudian pilih 'Continue'.

![konfigurasi proxy](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/22.setting_proxy.PNG)

- Pilih prefensi untuk menangani update yang akan terjadi kedepannya. Pilih 'No automatic updates' bila menginginkan sistem tidak melakukan update secara otomatis dan update dilakukan secara manual melalui package manager. Pilih 'Install security update automatically' bila menginginkan sistem mengupdate secara otomatis. Pilih 'Manage system with Landscape' bila mengingkan konfigurasi dan update sistem dilakukan dengan Landscape.

![pilih prefensi update sistem](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/23.pilih_setting_update.PNG)

- Pilih satu atau lebih software tambahan dari list untuk diinstal pada sistem.

![pilih software](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/24.pilih_software.PNG)

- Pilih satu atau lebih software tambahan dari list untuk diinstal pada sistem.

![pilih software](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/24.pilih_software.PNG)

- Bila Ubuntu Server yang akan diinstal merupakan satu-satunya OS yang terinstal pada komputer, maka anda akan mendapat pilihan untuk menginstal GRUB boot loader pada master boot record. Pilih 'Yes' untuk menginstal GRUB boot loader pada master boot record dan melanjutkan instalasi.

![GRUB boot loader pada master boot record](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/27.instalasi_grub_loader.PNG)

- Instalasi OS Ubuntu Server telah selesai dan dapat dioperasikan.

![instalasi selesai](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/28.instalasi_selesai.PNG)

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

- Bila ssh telah terinstal dengan baik maka perintah diatas akan menghasilkan 'ssh start/running'.

![hasil dari perintah service ssh status](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bssh%5D04.PNG)

### 4. Langkah Uji Penetrasi dengah SSH Brute Force Tools

## Uji Penetrasi 2

### 1. Langkah Konfigurasi Fail2ban

### 2. Langkah Konfigurasi SSH Server

### 3. Langkah Uji Penetrasi dengah SSH Brute Force Tools

## Kesimpulan dan Saran

