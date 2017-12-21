# CUCKOO SANDBOX

## Instalasi dan Konfigurasi
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

4. Install Yara
```
$ sudo apt-get install autoconf libtool libjansson-dev libmagic-dev libssl-dev -y
$ wget http://github.com/plusvic/yara/archive/v3.4.0.tar.gz -O yara-3.4.0.tar.gz
$ tar-zxf yara-3.4.0.tar.gz
$ cd yara-3.4.0
$ ./bootstrap.sh
$ ./configure --with-crypto --enable-cuckoo --enable-magic
$ make
$ sudo make install
$ yara -v
```

5. Menginstall ekstensi Yara
```
$ cd yara-python
$ python setup.py build
$ sudo python setup.py install
$ pip show yara-python
```

6. Menginstall Pydeep
```
$ wget http://sourceforge.net/projects/ssdeep/files/ssdeep-2.13.tar.gz/download -O ssdeep-2.13.tar.gz
$ tar -zxf ssdeep-2.13.tar.gz
$ cd ssdeep-2.13
$ ./configure
$ make
$ sudo make install
$ ssdeep -V
$ pip install pydeep
$ pip show pydeep
```

7. Menginstall Volatility yang merupakan tool optional untuk melakukan analisis forensik pada memori dumps




## Skenario
