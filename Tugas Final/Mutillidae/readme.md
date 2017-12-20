# Mutillidae

## Lesson 5 - Manual SQL Injection with Firebug
1. Jalankan Firefox pada BackTrack

2. Akses `http://ipmutillidae/mutillidae` dari Firefox. IP mutillidae yang digunakan adalah  <b>192.168.56.1</b> sehingga URL yang diakses menjadi `http://192.168.56.1/mutillidae`

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_01.png)

3. Klik Login/Register

4. Masukkan tanda <b>`(')`</b> pada textbox Name lalu klik Login

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_02.png)

5. Setelah itu akan muncul error message

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_03.png)

6. Ubah isi dari textbox name menjadi <b>`' or 1=1-- `</b>. Tambahkan spasi setelah karakter `-- `

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m5_04.png)




Refrensi: http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson5/index.html


## Lesson 8 - SQL Injection Union Exploit #1
1. Mencoba melakukan union dengan menggunakan database mutillidae
mysql -uroot -psamurai
use nowasp;
select * from accounts union select ccid,ccnumber,ccv,expiration,null from credit_card;

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Mutillidae/Screenshot/m7_02.jpg)

2. Mengakses mutillidae melalui browser dari backtrack
192.168.56.1/mutillidae

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
