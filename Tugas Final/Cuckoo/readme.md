# CUCKOO SANDBOX

## Instalasi
1. Instalasi Python Libraries
```
$ sudo apt-get install python python-pip python-dev libffi-dev libssl-dev
$ sudo apt-get install python-virtualenv python-setuptools
$ sudo apt-get install libjpeg-dev zlib1g-dev swig
```
2. Instalasi mongodb agar dapat menggunakan Django-based Web Interface
```
$ sudo apt-get install mongodb
```
3. Instalasi tcpdump
```
$ sudo apt-get install tcpdump apparmor-utils
$ sudo aa-disable /usr/sbin/tcpdump
```
Karena Cuckoo tidak harus berjalan di root tetapi tcpdump memerlukan root privileges maka lakukan setting berikut ini
```
sudo setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump
```
Jika setting berhasil maka jika perintah `getcap /usr/sbin/tcpdump` dijalankan maka akan muncul `/usr/sbin/tcpdump = cap_net_admin,cap_net_raw+eip`

### Instalasi Cuckoo


## Konfigurasi

## Skenario
