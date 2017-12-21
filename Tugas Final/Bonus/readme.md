# Snort

## Instalasi

1. Pada terminal masukkan perintah:

```
sudo apt install -y gcc libpcre3-dev zlib1g-dev libpcap-dev openssl libssl-dev libdumbnet-dev bison flex libdnet
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_01.png)

2. Kemudian masukkan perintah untuk membuat dan berpindah di direktori baru: ``` mkdir ~/snort_src && cd ~/snort_src ```
3. Untuk mendapatkan Data Acquisition library (DAQ) dari snort masukkan perintah:

```  wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_02.png)

4. Kemudian jalankan perintah untuk ekstarksi: ```  tar -xvzf daq-2.0.6.tar.gz ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_03.png)

5. Inputkan perintah ``` tar -xvzf daq-2.0.6.tar.gz ``` untuk berpindah lokasi.
6. Untuk menginstal DAQ jalankan perintah: ``` ./configure && make && sudo make install ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_04.png)

7. Pindah direktori dengan: ``` cd ~/snort_src ```
8. Inputkan perintah berikut untuk mendownload Snort 2.9.11: ``` wget https://www.snort.org/downloads/snort/snort-2.9.11.tar.gz ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_05.png)

9. Ekstrak file yang telah didownload: ``` tar -xvzf snort-2.9.9.0.tar.gz ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_06.png)

10. Pindak direktori pada folder hasil ekstraksi: ``` cd snort-2.9.11 ```
11. Untuk menginstal Snort jalankan perintah: ``` ./configure --enable-sourcefire && make && sudo make install ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/is_07.png)

## Konfigurasi

1. Update shared libraries dengan: ``` sudo ldconfig ```




