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
2. Snort terinstal pada direktori /usr/local/bin/snort directory, maka dibuat symbolic link ke /usr/sbin/snort:

``` sudo ln -s /usr/local/bin/snort /usr/sbin/snort ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/nidsconf_01.png)

### Setting username dan struktur folder

1. Untuk menjalankan Snort tanpa root, maka buat group & user baru:

``` 
sudo groupadd snort
sudo useradd snort -r -s /sbin/nologin -c SNORT_IDS -g snort
```

2. Buat struktur folder yang menjadi rumah dari configurasi Snort:

``` 
sudo mkdir -p /etc/snort/rules
sudo mkdir /var/log/snort
sudo mkdir /usr/local/lib/snort_dynamicrules
```

3. Memberi akses pada direktori baru:

``` 
sudo chmod -R 5775 /etc/snort
sudo chmod -R 5775 /var/log/snort
sudo chmod -R 5775 /usr/local/lib/snort_dynamicrules
sudo chown -R snort:snort /etc/snort
sudo chown -R snort:snort /var/log/snort
sudo chown -R snort:snort /usr/local/lib/snort_dynamicrules
```

4. Membuat rule black dan white list:

``` 
sudo touch /etc/snort/rules/white_list.rules
sudo touch /etc/snort/rules/black_list.rules
sudo touch /etc/snort/rules/local.rules
```

5. Mengkopi file configurasi dari folder download:

``` 
sudo cp ~/snort_src/snort-2.9.11/etc/*.conf* /etc/snort
sudo cp ~/snort_src/snort-2.9.11/etc/*.map /etc/snort
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/nidsconf_02.png)

### Menggunakan Community Rules

1. Untuk mendownload community rules, masukkan perintah:

``` wget https://www.snort.org/rules/community -O ~/community.tar.gz ```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/comconf_01.png)

2. Ekstrak rule dan pindahkan pada folder configurasi:

``` 
sudo tar -xvf ~/community.tar.gz -C ~/
sudo cp ~/community-rules/* /etc/snort/rules
```

3. Kemudian jalankan perintah:

``` sudo sed -i 's/include \$RULE\_PATH/#include \$RULE\_PATH/' /etc/snort/snort.conf ```

### Konfigurasi rule jaringan

1. Buka file snort.conf dengan perintah: ``` sudo gedit /etc/snort/snort.conf ```
2. Ubah file tersebut dengan menambahkan berikut pada tempatnya:

``` 
# Path to your rules files (this can be a relative path)
var RULE_PATH /etc/snort/rules
var SO_RULE_PATH /etc/snort/so_rules
var PREPROC_RULE_PATH /etc/snort/preproc_rules

``` 

``` 
# Set the absolute path appropriately
var WHITE_LIST_PATH /etc/snort/rules
var BLACK_LIST_PATH /etc/snort/rules
``` 

``` 
# unified2
# Recommended for most installs
output unified2: filename snort.log, limit 128
```

``` 
include $RULE_PATH/local.rules
include $RULE_PATH/community.rules
```

### Validasi Konfigurasi

1. Untuk memfalidasi konfigurasi Snort, maka jalankan snort dengan mode Test:

``` 
sudo snort -T -c /etc/snort/snort.conf
```

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/conf_01.png)


## Membaca Pcap

1. Download file Pcap yang ingin digunakan pada:

``` 
http://www.secrepo.com/
```

2. Bila lebih dari 1 file pcap, maka letakkan dalam 1 folder untuk mempermudah:
3. Jalankan perintah berikut untuk 1 file: 

``` 
snort -r nama_file_pcap.pcap
atau snort --pcap-single=nama_file_pcap.pcap
``` 

4. Atau jalankan perintah berikut untuk banyak file:

``` 
sudo snort -v -i etho0 -c /etc/snort/snort.conf snort --pcap-filter="*.pcap" --pcap-dir=/home/kartuhitam/Downloads/opclever
``` 

![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/snort_00.png)
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/snort_01.png)
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/snort_02.2.png)
![](https://raw.githubusercontent.com/dns-148/PKSJ/master/Tugas%20Final/Bonus/Screenshot/snort_03.png)









