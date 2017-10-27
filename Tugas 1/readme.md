# Tugas 1 - Uji Penetrasi

#### Anggota Kelompok
- Tionia Rizkika (5114100053)
- Destiana Nurliasari (5114100148)
- Afifah Asmar Sari (5114100154)

- - - -

## Pendahuluan
Keamanan jaringan adalah suatu cara atau suatu sistem yang digunakan untuk memberikan proteksi atau perlindungan pada suatu jaringan agar terhindar dari berbagai ancaman luar yang mampu merusak jaringan. Salah satu contoh dari ancaman terhadap keamanan suatu jaringan adalah dengan adanya penetrasi pada SSH server. Password cracking merupakan salah satu teknik dalam melakukan penetrasi. Pada uji penetrasi kali ini, akan dilakukan pengujian password cracking menggunakan tools SSH brute force attack. Selain itu, akan dilakukan juga pengujian password cracking yang akan dicountermeasure menggunakan beberapa tools yang digunakan untuk menangkal serangan brute force.

## Dasar Teori

### Ubuntu Server
Ubuntu Server adalah sistem operasi turunan dari Linux Ubuntu yang di desain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai sistem operasi server. Pada Ubuntu Server tidak terdapat GUI dan hanya menggunakan CLI (Command Line Interface). Ubuntu Server menyediakan platform yang dapat memudahkan proses deploy server dengan fasilitas layanan internet standar, seperti mail, web, DNS, file-serving, hingga manajemen database. Ubuntu Server tidak membiarkan keberadaan port terbuka setelah proses instalasi, dan hanya akan memuat software yang dibutuhkan untuk membangun sebuah sistem server yang aman.

### Ubuntu Desktop
Ubuntu merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai software bebas. Ubuntu Desktop ditujukan untuk user yang memakai Ubuntu sebagai end user. Pada Ubuntu Desktop telahterinstall beberapa aplikasi, diantaranya: LibreOffice, Mozilla Firefox, dan Mozilla Thunderbird. Ubuntu Desktop mengompile paket menggunakan fitur gcc seperti PIE dan proteksi Buffer Overflow untuk memproteksi software.

### OpenSSH Server
OpenSSH adalah satu set aplikasi komputer yang bisa mendukung sesi komunikasi terenkripsi pada jaringan komputer menggunakan protokol ssh. Awalnya aplikasi ini dikembangkan sebagai aplikasi open source yang menjadi alternatif dari aplikasi serupa yang berbayar. OpenSSH dikembangkan dan merupakan bagian dari proyek OpenBSD. Dalam perkembangan selanjutnya, OpenSSH tidak hanya memberikan aplikasi remote shell melalui ssh atau remote eksekusi program saja, tapi bisa digunakan untuk tunnelling atau setup vpn antara dua jaringan.

### THC-Hydra
THC-Hydra adalah login cracker paralel yang mendukung penyerangan terhadap berbagai macam protokol. THC-Hydra sangat cepat dan fleksibel, dan mudah untuk menambahkan modul-modul baru. Tool ini memungkinkan para peneliti dan konsultan keamanan untuk menunjukkan betapa mudahnya mendapatkan akses yang tidak sah ke sistem dari jarak jauh.

THC-Hydra mendukung: Cisco AAA, Cisco auth, Cisco enable, CVS, FTP, HTTP(S)-FORM-GET, HTTP(S)-FORM-POST, HTTP(S)-GET, HTTP(S)-HEAD, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MySQL, NNTP, Oracle Listener, Oracle SID, PC-Anywhere, PC-NFS, POP3, PostgreSQL, RDP, Rexec, Rlogin, Rsh, SIP, SMB(NT), SMTP, SMTP Enum, SNMP v1+v2+v3, SOCKS5, SSH (v1 and v2), SSHKEY, Subversion, Teamspeak (TS2), Telnet, VMware-Auth, VNC and XMPP.

### Ncrack
Ncrack adalah tool untuk cracking otentikasi jaringan berkecepatan tinggi. Ncrack dibangun untuk membantu perusahaan mengamankan jaringan mereka dengan cara pro-aktif menguji semua host dan perangkat jaringan mereka dengan kata kunci yang buruk. Profesional dibidang keamanan juga mengandalkan Ncrack untuk mengaudit klien mereka. Ncrack dirancang menggunakan pendekatan modular, command-line syntax yang mirip dengan Nmap dan mesin dinamis yang dapat menyesuaikan perilakunya berdasarkan umpan balik jaringan. Ini memungkinkan dilakukannya audit berskala besar yang cepat namun dapat diandalkan untuk beberapa host.

Fitur Ncrack mencakup antarmuka yang sangat fleksibel yang memberi pengguna kontrol penuh atas operasi jaringan, memungkinkan serangan bruteforcing yang sangat canggih, template waktu untuk kemudahan penggunaan, interaksi runtime yang mirip dengan Nmap dan banyak lagi. Protokol yang didukung meliputi RDP, SSH, HTTP (S), SMB, POP3 (S), VNC, FTP, SIP, Redis, PostgreSQL, MySQL, dan Telnet.

### Medusa
Medusa adalah sebuah agen brute-force login yang cepat, sangat paralel, modular bagi layanan jaringan. Medusa diciptakan oleh para ahli di Foofus.net. Tujuan dibuatnya Medusa adalah untuk mendukung sebanyak mungkin layanan yang memungkinkan otentikasi jarak jauh. Beberapa fitur yang mejadi fitur penting dari Medusa adalah sebagai berikut: thread-based parallel testing, input pengguna yang flexibel, dan desain yang modular. 

Saat ini Medusa memiliki modul untuk layanan berikut: CVS, FTP, HTTP, IMAP, MS-SQL, MySQL, NCP (NetWare), PcAnywhere, POP3, PostgreSQL, rexec, rlogin, rsh, SMB, SMTP (VRFY), SNMP, SSHv2 , SVN, Telnet, VmAuthd, VNC, dan modul pembungkus generik.

### Fail2Ban
Fail2Ban adalah framework perangkat lunak pencegah intrusi untuk melindungi komputer server dari serangan brute-force. Perangkat lunak ini ditulis dengan menggunakan bahasa pemrograman python dan dapat berjalan pada POSIX sistem yang memiliki interface pada sistem kotrol-paket atau firewall yang terinstal secaral lokal, seperti iptables atau TCP Wrapper.

Fail2Ban beroperasi dengan memonitor file log (misalnya pada /var/log/auth.log, /var/log/apache/access.log, dll.) untuk entri yang dipilih dan menjalankan skrip berdasarkan entri tersebut. Umumnya ini digunakan untuk memblokir alamat IP terpilih yang kemungkinan merupakan milik host yang mencoba menerobos keamanan sistem. Fail2Ban dapat melarang setiap alamat IP host yang melakukan percobaan login terlalu banyak atau melakukan tindakan lain yang tidak diinginkan dalam jangka waktu yang ditentukan oleh administrator.

### DenyHosts
DenyHosts adalah script python yang menganalisis sshd server log message untuk menentukan host mana yang mencoba untuk melakukan hacking pada suatu sistem dan menentukan user account mana yang menjadi targetnya. DenyHosts melacak frekuensi dari percobaan hacking yang dilakukan oleh tiap host. File /etc/hosts.deny akan diperbarui untuk mencegah percobaan peretasan dari suatu host di masa mendatang.

### Sshguard
Sshguard memproteksi host dari brute-force attack pada SSH dan servis-servis lain. Sshguard mengagregasi system logs dan memblokir penyerang yang melakukan serangan beberapa kali menggunakan satu atau lebih firewall backends, diantaranya iptables, ipfw, dan pf.
Sshguard dapat membaca log message dari input standar (cocok untuk piping dari syslog) atau memonitor satu atau lebih log file. Log message akan diparsing tiap barisnya untuk mengenali pola. Jika suatu serangan, misalnya beberapa kegagalan login dalam jangka waktu yang singkat terdeteksi, maka IP dari penyerang akan diblokir.


## Uji Penetrasi 1

### 1. Langkah Instalasi Ubuntu Server

- Pilih bahasa untuk menu installasi.

![menu pilih bahasa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/1.pilih_bahasa.PNG)

- Pilih 'Install Ubuntu Server' pada menu installasi.

![pilih install](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/2.pilih_install_ubuntu_server.PNG)

#### Konfigurasi bahasa, lokasi dan sistem lokal

- Pilih bahasa untuk OS Ubuntu Server.

![pilih bahasa OS](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/3.pilih_bahasa_ubuntu_server.PNG)

- Pilih lokasi yang nanti akan digunakan saat menentukan timezone dan system locale.

![pilih lokasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/4.pilih_lokasi.PNG)

- Bila dari kombinasi antara bahasa OS yang dipilih dan lokasi yang dipilih tidak ditemukan locale yang tepat, maka pengguna dapat memilih locale secara manual.

![pilih locale](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/5.pilih_konfigurasi_lokal.PNG)

#### Konfigurasi keyboard layout

- Konfigurasi layout dari keyboard, pilih 'Yes' bila ingin melakukan test untuk mendapatkan layout keyboard, pilih 'No' untuk memilih layout yang disediakan.

![pilih layout keyboard](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/6.konfigurasi_keyboard.PNG)

- Bila memilih 'Yes', maka akan muncul serangkaian test untuk mencocokan character yang ditampilkan dengan yang berada pada keyboard. Kemudian dari hasil test tersebut didapatkan layout keyboard.

![hasil test keyboard](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/7.konfigurasi_keyboard2.PNG)

#### Konfigurasi data pengguna

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

#### Konfigurasi timezone

- Timezone telah dipilih secara otomatis dari lokasi fisik komputer yang sedang melakukan instalasi. Bila hasil pemilihan benar, pilih 'Yes' untuk melanjutkan instalasi. Bila hasil kurang sesuai, pilih 'No' untuk memilih timezone secara manual dari list.

![pengaturan timezone](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/15.setting_up_clock.PNG)

- Bila memilih 'No' pada pilihan sebelumnya, sekarang anda akan memilih manual timezone dari list yang disediakan.

![pilih timezone](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/16.setting_up_clock.PNG)

#### Partisi disk

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

#### Konfigurasi package manager

- Bila diperlukan proxy untuk mengakses internet, maka inputkan informasi HTTP proxy dan bila tidak maka dapat dikosongkan. Kemudian pilih 'Continue'.

![konfigurasi proxy](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/22.setting_proxy.PNG)

- Pilih prefensi untuk menangani update yang akan terjadi kedepannya. Pilih 'No automatic updates' bila menginginkan sistem tidak melakukan update secara otomatis dan update dilakukan secara manual melalui package manager. Pilih 'Install security update automatically' bila menginginkan sistem mengupdate secara otomatis. Pilih 'Manage system with Landscape' bila mengingkan konfigurasi dan update sistem dilakukan dengan Landscape.

![pilih prefensi update sistem](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/23.pilih_setting_update.PNG)

- Pilih satu atau lebih software tambahan dari list untuk diinstal pada sistem.

![pilih software](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/24.pilih_software.PNG)

#### GRUB boot loader

- Bila Ubuntu Server yang akan diinstal merupakan satu-satunya OS yang terinstal pada komputer, maka anda akan mendapat pilihan untuk menginstal GRUB boot loader pada master boot record. Pilih 'Yes' untuk menginstal GRUB boot loader pada master boot record dan melanjutkan instalasi.

![GRUB boot loader pada master boot record](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/27.instalasi_grub_loader.PNG)

- Instalasi OS Ubuntu Server telah selesai dan dapat dioperasikan.

![instalasi selesai](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/28.instalasi_selesai.PNG)

### 2. Langkah Instalasi Ubuntu Desktop

- Pilih 'Install Ubuntu' untuk memulai instalasi OS Ubuntu Desktop.

![mulai instalasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D01.png)

- Pastikan komputer yang akan diinstal OS Ubuntu memiliki ukuran drive lebih dari 6.7 GB, tersambung pada sumber daya, dan terkoneksi dengan internet untuk proses instalasi yang lancar. Centang 'Download update while installing' bila menginginkan update dari sistem terdownload pada saat instalasi OS.

![persyaratan instalasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D02.png)

- Bila tidak memiliki OS lainnya yang terinstal, maka pilih 'Erase disk and install Ubuntu' dan centang 'Use LVM with the new Ubuntu installantion' bila menginginkan Logical Volume Manager. Pilih 'Continue'.

![partisi disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D03.png)

- Pop-up konfirmasi tentang informasi perubahan yang akan terjadi pada disk. Pilih 'Continue' jika telah setuju akan rencana perubahan yang akan terjadi. Pilih 'Go Back' untuk kembali ke langkah sebelumnya.

![konfirmasi partisi disk](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D03_2.png)

- Input lokasi anda dan pilih 'Continue'.

![pilih lokasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D04_2.png)

- Pilih keyboard layout secara manual yang tersedia di list atau secara otomatis dengan melakukan test keyboard pada 'Detect Keyboard Layout'. Kemudian pilih 'Continue'.

![pilih keyboard layout](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D05.png)

- Input data informasi tentang pengguna seperti: nama lengkap, nama komputer, username dan password. Kemudian pilih 'Continue'.

![input informasi user](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D06_1.png)

- Proses instalasi OS Ubuntu Desktop akan berjalan, tunggu hingga proses tersebut selesai dengan tidak mematikan komputer secara paksa.

![proses instalasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D07.png)

- OS Ubuntu Desktop berhasil diinstal, restart komputer untuk menggunakan OS yang telah terinstal.

![instalasi selesai](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/%5Bdesktop%5D08.png)


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

- Username pada SSH server yang menjadi target: **afifahas**
- Password dari user target: **AfifahAS01**
- IP dari SSH server: **192.168.56.101**
- File yang berisi daftar password: **pass.txt**
  - Isi dari file yang **tidak mengandung** password dari user target
    ![pass_salah](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/pass_salah.JPG)
  - Isi dari file yang **mengandung** password dari user target
    ![pass_benar](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/pass_benar.JPG)

#### THC-Hydra
1. Install THC-Hydra pada Ubuntu Desktop

<pre>
sudo apt-get install hydra
</pre>

2. Siapkan sebuah file .txt pada Ubuntu Desktop yang berisi daftar kemungkinan password dari user target.

3. Lakukan pengujian brute force attack dengan memasukkan perintah berikut

<pre>
hydra -l username -P daftar-password.txt ip-ssh-server ssh
</pre>

  - Pengujian pertama dilakukan dengan menggunakan file .txt yang tidak mengandung password yang benar dari user target.

    Hasil dari pengujian pertama:
    
    ![hydra_password_tidak_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]hydra_fail.JPG)
  
  - Pengujian kedua dilakukan dengan menggunakan file .txt yang mengandung password yang benar dari user target.
    
    Hasil dari pengujian kedua:
    
    ![hydra_password_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]hydra_success.JPG)

#### Ncrack

1. Install Ncrack pada Ubuntu Desktop

<pre>
wget https://nmap.org/ncrack/dist/ncrack-0.5.tar.gz
./configure
make
make install
</pre>

2. Siapkan sebuah file .txt pada Ubuntu Desktop yang berisi daftar kemungkinan password dari user target.

3. Lakukan pengujian brute force attack dengan memasukkan perintah berikut

<pre>
ncrack -p port-ssh-server --user username -P daftar-password.txt ip-ssh-server
</pre>

 - Pengujian pertama dilakukan dengan menggunakan file .txt yang tidak mengandung password yang benar dari user target.

    Hasil dari pengujian pertama:
    
    ![ncrack_password_tidak_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]ncrack_fail.JPG)
  
  - Pengujian kedua dilakukan dengan menggunakan file .txt yang mengandung password yang benar dari user target.
    
    Hasil dari pengujian kedua:
    
    ![ncrack_password_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]ncrack_success.JPG)

#### Medusa

1. Install Medusa pada Ubuntu Desktop

<pre>
sudo apt-get install medusa
</pre>

2. Siapkan sebuah file .txt pada Ubuntu Desktop yang berisi daftar kemungkinan password dari user target.

3. Lakukan pengujian brute force attack dengan memasukkan perintah berikut

<pre>
medusa -u username -P daftar-password.txt ip-ssh-server -M ssh
</pre>

 - Pengujian pertama dilakukan dengan menggunakan file .txt yang tidak mengandung password yang benar dari user target.

    Hasil dari pengujian pertama:
    
    ![medusa_password_tidak_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]medusa_fail.JPG)
  
  - Pengujian kedua dilakukan dengan menggunakan file .txt yang mengandung password yang benar dari user target.
    
    Hasil dari pengujian kedua:
    
    ![medusa_password_ditemukan](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji1]medusa_success.JPG)


## Uji Penetrasi 2

### 1.	Setting SSH Server agar tidak menggunakan setting default

Upaya untuk mengamankan SSH Server dapat dilakukan dengan berbagai cara, 2 diantara adalah dengan mengganti port server dan menonaktifkan password authentication. Keduanya dilakukan dengan melakukan perubahan pada `sshd_config` yang terdapat pada direktori `/etc/ssh` dan harus diakses menggunakan root.

#### Mengubah port server
  - Buka file `sshd_config` dengan mengetikkan command sebagai berikut :
    
    <pre>
    sudo nano /etc/ssh/sshd_config
    </pre>
    
  - Lakukan perubahan pada bagian port. Secara default port dari ssh server adalah 22 dan kebanyakan brute force attacks akan menyerang langsung port 22 tersebut. Kita dapat mengganti port 22 dengan port lain yang belum terdaftar sebagai service, misalkan **2200**.
  - Simpan perubahan dan lakukan restart terhadap server dengan mengetikkan command sebagai berikut :
    
    <pre>
    sudo service ssh restart
    </pre>
  - Kemudian jalankan brute force attacks maka akan menghasilkan error sebagai berikut :
    
    **Hydra**
    
    ![ubah_port_hydra](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]port_hydra.JPG)
    
    **Ncrack**
    
    ![ubah_port_ncrack](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]port_ncrack.JPG)
    
    **Medusa**
    
    ![ubah_port_Medusa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]port_medusa.JPG)

#### Menonaktifkan password authentication

Untuk menggunakan settingan ini tidak bisa sembarangan, hal ini dapat dilakukan jika user bersangkutan sudah login dan ingin mengamankan ssh servernya. Karena apabila user melakukan log out tanpa merubah settingan terlebih dahulu, maka user bersangkutan juga tidak dapat melakukan login dengan password. Settingan ini dilakukan secara permanen apabila telah menggunakan public/private key sebagai pengganti password.
  - Buka file `sshd_config` dengan mengetikkan command sebagai berikut :

    <pre>
    sudo nano /etc/ssh/sshd_config
    </pre>
    
  - Hilangkan tanda **#** pada bagian **PasswordAuthentication** dan ubah statusnya menjadi **no**
    
  - Simpan perubahan dan lakukan restart terhadap server dengan mengetikkan command sebagai berikut :
    <pre>
    sudo service ssh restart
    </pre>
  - Kemudian jalankan brute force attacks maka akan menghasilkan error sebagai berikut :
    **Hydra**
    ![ubah_passauth_hydra](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]pass_hydra.JPG)
    
    **Ncrack**
    ![ubah_passauth_ncrack](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]pass_ncrack.JPG)
    
    **Medusa**
    ![ubah_passauth_medusa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]pass_medusa.JPG)
    
### 2.	Fail2Ban

Settingan pada fail2ban dilakukan pada `jail.conf` akan tetapi banyak referensi yang menyarankan untuk merubah settingan pada `jail.local` dibandingkan `jail.conf`. Berikut langkah-langkahnya :

- Terdapat 2 parameter yang perlu diperhatikan yakni :
  - Bantime = **600** (jangka waktu ban)
  - Findtime = **100** (jangka waktu ujicoba login)
  - Maxtry = **3** (jumlah maksimal ujicoba login)
  
- Simpan konfigurasi dan lakukan restart fail2ban yakni dengan :
  <pre>
  sudo service fail2ban restart
  </pre>

- Kemudian jalankan brute force attacks maka akan menghasilkan error sebagai berikut :
  **Hydra**
  ![fail2ban_hydra](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]fail2ban_hydra.JPG)
    
  **Ncrack**
  ![fail2ban_ncrack](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]fail2ban_ncrack.JPG)
    
  **Medusa**
  ![fail2ban_medusa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]fail2ban_medusa.JPG)

### 3.	SSHGuard
Berikut langkah-langkah konfigurasi SSHGuard :
- Melakukan iptables
  <pre>
  iptables -N SSHGuard
  </pre>
- Untuk melakukan block pada SSH, FTP, POP, IMAP gunakan multiport modul dengan mengetikkan command berikut :
  <pre>
  iptables -A INPUT -m multiport -p tcp –destination-ports 21,22,110,143 -j SSHGuard
  </pre>
- Untuk melakukan block pada hal yang dianggap mencurigakan oleh SSHGuard ketikkan command sebagai berikut :
  <pre> 
  iptables -A INPUT -j SSHGuard
  </pre>
- Kemudian jalankan brute force attacks maka akan menghasilkan error sebagai berikut :
  **Hydra**
  ![sshguard_hydra](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]sshguard_hydra.JPG)
    
  **Ncrack**
  ![sshguard_ncrack](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]sshguard_ncrack.JPG)
    
  **Medusa**
  ![sshguard_medusa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]sshguard_medusa.JPG)

### 4.	DenyHosts
Langkah-langkah melakukan konfigurasi pada denyhosts adalah sebagai berikut :
- Buka file `denyhosts.conf` dengan mengetikkan command seperti berikut :
- Pastikan :
  <pre>
  SECURE_LOG = /var/log/auth.log
  HOSTS_DENY = /etc/hosts.deny
  BLOCK_SERVICE = sshd
  </pre>
- Atur `DENY_THRESHOLD_INVALID` untuk melakukan limitasi terhadap kegagalan usaha login pada akun yang tidak terdaftar. By default nilainya adalah **1**.
- Atur `DENY_THRESHOLD_VALID` untuk melakukan limitasi terhadap kegagalan usaha login pada akun yang terdaftar. By default nilainya adalah **3**.
-	Atur `DENY_THRESHOLD_ROOT` untuk melakukan limitasi usaha login pada akun root. By default nilainya adalah **1**.
- Simpan konfigurasinya dan jalankan brute force attacks maka akan dihasilkan error sebagai berikut :
  **Hydra**
  ![denyhosts_hydra](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]denyhosts_hydra.JPG)
    
  **Ncrack**
  ![denyhosts_ncrack](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]denyhosts_ncrack.JPG)
    
  **Medusa**
  ![denyhosts_medusa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%201/Screenshot/[uji2]denyhosts_medusa.JPG)


## Kesimpulan dan Saran

### Kesimpulan
Walaupun memang brute force attacks merupakan serangan sederhana yang dapat ditanggulangi dengan tools yang banyak tersedia akan tetapi perlu selalu diwaspadai keberadaannya.

### Saran
- Selalu pastikan security untuk server terkonfigurasi dengan baik dan benar. Seperti dengan mengubah pengaturan SSH server dan dengan menambahkan tools untuk mengamankan server.
- Apapun tools security yang digunakan perlu dipastikan pula kegunaan dan peruntukannya agar dapat berjalan maksimal.

