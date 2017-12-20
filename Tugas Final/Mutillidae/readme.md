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

7. 

Referensi : http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson8/index.html
