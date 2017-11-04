# Tugas 2 - SQL Injection

#### Anggota Kelompok
- Tionia Rizkika (5114100053)
- Destiana Nurliasari (5114100148)
- Afifah Asmar Sari (5114100154)

- - - -

## Pendahuluan

## Dasar Teori

### OS yang Digunakan

#### Ubuntu Desktop
Ubuntu merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai software bebas. Ubuntu Desktop ditujukan untuk user yang memakai Ubuntu sebagai end user. Pada Ubuntu Desktop telahterinstall beberapa aplikasi, diantaranya: LibreOffice, Mozilla Firefox, dan Mozilla Thunderbird. Ubuntu Desktop mengompile paket menggunakan fitur gcc seperti PIE dan proteksi Buffer Overflow untuk memproteksi software.

### Wordpress Plugin yang Digunakan

#### 1. VideoPlayer 1.5.16
Merupakan Plugin yang digunakan untuk menambahkan video pada Wordpress website. Pada plugin ini terdapat fitur untuk membuat playlist video, mengatur layout dan tampilan dari player dan terintegrasi dengan beberapa media sosial (Facebook, Google+ dan Twitter). Plugin ini dapat diunduh pada https://wordpress.org/plugins/player/

#### 2. LeagueManager 3.9.1.1
Merupakan plugin yang digunakan untuk mengatur dan menampilkan hasil dari pertandingan olahraga pada Wordpress website. Plugin ini dapat diunduh pada https://wordpress.org/plugins/leaguemanager/

#### 3. Simply Polls 1.4.1
Merupakan plugin yang digunakan untuk membuat poll pada Wordpress website. Poll yang dibuat dapat ditampilkan pada sidebar, post, maupun pages dari website. Plugin ini dapat diunduh pada https://wordpress.org/plugins/simply-polls/

### Tools yang Digunakan

#### 1. WPScan
Merupakan tools untuk melihat celah keamanan dari seluruh plugin dan theme yang digunakan pada Wordpress website. Tools ini dibuat menggunakan bahasa ruby.

#### 2. sqlmap
Merupakan tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server.

## Instalasi

### Langkah Instalasi Wordpress
- Download Wordpress dari alamat: <pre>https://wordpress.org/download/</pre>
- Extract hasil file hasil dari download pada directori home, bila menggunakan OS Windows dan XAMPP maka directori default ada pada: <pre>C:\xampp\htdocs\ </pre>
- (Opsional) Rename folder hasil extract bila diperlukan.
- Buka file **'wp-config-sample.php'** menggunakan text-editor, ubah pengaturan database sesuai dengan kehendak:
![atur database](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wp-configPNG.PNG)
- Untuk mengubah url, tambahkan: <pre>
define('WP_HOME',    'http://alamatip/nama_folder');
define('WP_SITEURL', 'http://alamatip/nama_folder');
</pre>

- Simpan dan ubah nama menjadi **'wp-config.php'**.
- Pada browser buka url yang telah di inputkan sebelumnya pada **'wp-config.php'**, seperti: <pre>
http://192.168.100.19/wordpress/ -> (http://alamatip/nama_folder)
</pre>

- Pilih bahasa instalasi:

![pilih bahasa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step1.PNG)

- Input data user dan web:

![data user](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step2.PNG)

- Instalasi wordpress telah selesai, untuk menggunakan mengatur wordpress login dengan mengklik button 'Login' atau pada alamat:<pre>http://alamatip/nama_folder/wp-login/ </pre>

![instalasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step3.PNG)

### Langkah Instalasi Wordpress Plugin

## Uji Coba

### WPScan

- Buka terminal pada folder dimana wpscan berada, jalankan perintah:<pre>
ruby wpscan.rb --url alamat_site  --enumerate vp
</pre>
       Parameter `vp` pada `--enumerate` untuk memunculkan hasil plugin yang vulnerable.

- Hasil dari WPScan:

![hasil 1](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscanrun1.png)
![hasil 2](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscanresult1.png)

### sqlmap

## Kesimpulan dan Saran

### Kesimpulan

### Saran


