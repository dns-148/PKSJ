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


#### 2. LeagueManager 3.9.1.1
Merupakan plugin yang digunakan untuk mengatur dan menampilkan hasil dari pertandingan olahraga pada wordpress blog. Plugin dapat diunduh dari https://wordpress.org/plugins/leaguemanager/


#### 3. Simply Poll 1.4.1

### Tools yang Digunakan

#### 1. WPScan

#### 2. sqlmap





## Instalasi

### Langkah Instalasi Wordpress
- Download Wordpress dari alamat: <pre>https://wordpress.org/download/</pre>
- Extract hasil file hasil dari download pada directori home, bila menggunakan XAMPP directori default adalah pada: <pre>C:\xampp\htdocs\ </pre>
- (Opsional) Rename folder hasil extract bila diperlukan.
- Buka file 'wp-config-sample.php' menggunakan text-editor, ubah pengaturan database sesuai dengan kehendak:
![atur database](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wp-configPNG.PNG)
- Untuk mengubah url, tambahkan: <pre>
define('WP_HOME',    'http://alamatip/nama_folder');
define('WP_SITEURL', 'http://alamatip/nama_folder');
</pre>

- Simpan dan ubah nama menjadi 'wp-config.php'.
- Pada browser buka url yang telah di inputkan sebelumnya pada 'wp-config.php', seperti:
<pre>
http://192.168.100.19/wordpress/ -> (http://alamatip/nama_folder)
</pre>

- Pilih bahasa instalasi:
![pilih bahasa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step1.PNG)


### Langkah Instalasi Wordpress Plugin

## Uji Coba

## Kesimpulan dan Saran

### Kesimpulan

### Saran


