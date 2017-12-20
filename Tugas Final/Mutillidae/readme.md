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
