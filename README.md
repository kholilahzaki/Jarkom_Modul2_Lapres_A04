# Jarkom_Modul2_Lapres_A04

Kelompok A04:
-
#### I Gusti Agung Chintya Prema Dewi   (05111840000130)
#### Kholilah Zaki Lismia               (05111840000159)

## Soal:
Semeru adalah salah satu gunung yang terkenal di Jawa Timur. Bibah adalah salah satu juru kunci
Semeru. Bibah ingin menyebarkan keindahan Semeru pada dunia sehingga dia membeli 3 buah server
yang berada di MALANG, MOJOKERTO dan PROBOLINGGO. Server MALANG akan digunakan
sebagai DNS Server Master, MOJOKERTO akan digunakan sebagai DNS Server Slave dan
PROBOLINGGO akan digunakan sebagai Web Server. Selain 3 server terdapat 2 klien yang digunakan
untuk testing oleh Bibah yaitu GRESIK dan SIDOARJO. Untuk menyambungkan semua jaringan
tersebut Bibah memberi router di SURABAYA.

Kalian diminta untuk membuat sebuah website utama dengan 
- (1) alamat http://semeruyyy.pw yang memiliki, 
- (2) alias http://www.semeruyyy.pw, dan 
- (3) subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO serta dibuatkan, 
- (4) reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan
- (5) DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 
- (6) subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP
Server PROBOLINGGO. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 
- (7) subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO.
Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server.
- (8) Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw. Awalnya web dapat diakses menggunakan 
alamat http://semeruyyy.pw/index.php/home. Karena dirasa alamat urlnya kurang bagus, maka 
- (9) diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.
- (10) Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot 
pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut:

<p align="center"><img width="auto" src="https://user-images.githubusercontent.com/61299072/98775025-d8367b00-241e-11eb-99ad-dc311a339319.PNG"></p>

- (11) Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 
- (12) Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache. 
- (13) Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts.
Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.
Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 
- (14) sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada
/var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private 
- (15) Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya
aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default 
Apache yang bertuliskan “It works!”. 
- (16) Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan
secara otomatis ke http://semeruyyy.pw. 
- (17) Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar
yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

## Jawaban:
Sebelum mengerjakan soal No.1 ikuti langkah-langkah yang ada pada modul UML.

- [Jawaban No.1](#No.-1)
- [Jawaban No.2](#No.-2)
- [Jawaban No.3](#No.-3)
- [Jawaban No.4](#No.-4)
- [Jawaban No.5](#No.-5)
- [Jawaban No.6](#No.-6)
- [Jawaban No.7](#No.-7)
- [Jawaban No.8](#No.-8)
- [Jawaban No.9](#No.-9)
- [Jawaban No.10](#No.-10)
- [Jawaban No.11](#No.-11)
- [Jawaban No.12](#No.-12)
- [Jawaban No.13](#No.-13)
- [Jawaban No.14](#No.-14)
- [Jawaban No.15](#No.-15)
- [Jawaban No.16](#No.-16)
- [Jawaban No.17](#No.-17)

### No. 1
------------------------
**Membuat domain dengan alamat http://semerua04.pw** 
- Langkah pertama adalah buka UML Malang dan ketikkan:
```
nano /etc/bind/named/conf/local
```

- setelah itu isikan konfigurasi sebagai berikut:
```
zone "semerua04.pw" {
        type master;
        file "/etc/bind/jarkom/semerua04.pw";
};
```
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98776468-8cd19c00-2421-11eb-8da2-5b761aea4444.png"></p><br>

- Buat folder **jarkom** didalam `/etc/bind`
```
mkdir /etc/bind/jarkom
```
- Setelah itu copykan file db.local pada `/etc/bind` ke dalam folder **jarkom** yang baru saja dibuat dan ubah namanya menjadi **semerua04.pw** dengan perintah sebagai berikut
```
cp /etc/bind/db.local /etc/bind/jarkom/semerua04.pw
```
- Lalu buka file **semerua04.pw** dan edit dengan menggunakan IP PROBOLINGGO sebagai berikut
```
nano /etc/bind/jarkom/jarkom2020.com
```
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98785853-d3c68e00-242f-11eb-9a53-fe94c9099ca0.PNG"></p><br>
- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

### No. 2
----------------------------
**Membuat alias domain dengan alamat http://www.semerua04.pw**

Kemudian untuk membuat alias, dapat dilakukan dengan cara menggunakan CNAME dan edit file **semerua04.pw** seperti gambar berikut
<p align="center"><img width="auto" src="https://user-images.githubusercontent.com/61299072/98786005-0bcdd100-2430-11eb-9d44-347772b38bf9.PNG"></p><br>
Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate  

### No. 3
--------------------------
**Membuat subdomain pada MALANG yanng mengarah ke IP Server PROBOLINGGO dengan nama http://penanjakan.semerua04.pw**

Untuk pembuatan subdomain edit file `/etc/bind/jarkom/semerua04.pw` lalu tambahkan konfigurasi seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98784988-80077500-242e-11eb-891f-3e29657890e5.png"></p><br>
Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

### No. 4
-------------------------
**Membuat reverse DNS**
- Edit file `/etc/bind/named.conf.local` pada MALANG dengan cara sebagai berikut
```
nano /etc/bind/named.conf.local
```

- Lalu tambahkan konfigurasi sebagai berikut

```
zone "73.151.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/73.151.10.in-addr.arpa";
};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98788306-44bb7500-2433-11eb-9ece-0d18631ca609.png"></p><br>

- Copykan file db.local pada path `/etc/bind` ke dalam folder jarkom yang baru saja dibuat dan ubah namanya menjadi `73.151.10.in-addr.arpa` dengan cara sebagai berikut

```
cp /etc/bind/db.local /etc/bind/jarkom/73.151.10.in-addr.arpa
```

- Setelah itu edit file `73.151.10.in-addr.arpa` dengan mengetikkan `nano /etc/bind/jarkom/73.151.10.in-addr.arpa` seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98788764-ecd13e00-2433-11eb-9bf7-255255f2f83d.png"></p><br>

### No. 5
-------------------------
**Membuat DNS Server Slave pada MOJOKERTO**
- Pertama ubah konfigurasi file `/etc/bind/named.conf.local` pada server MALANG dengan syntax berikut

```
zone "semerua04.pw" {
    type master;
    notify yes;
    also-notify { 10.151.73.43; }; //IP MOJOKERTO
    allow-transfer { 10.151.73.43; }; //IP MOJOKERTO
    file "/etc/bind/jarkom/semerua04.pw";
};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98789714-3e2dfd00-2435-11eb-9539-0d8b0c072d13.png"></p><br>

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

- Lalu buka file /etc/bind/named.conf.local apad MOJOKERTO dan tambahkan sytax berikut:
```
zone "semerua04.pw" {
        type slave;
        masters { 10.151.73.42; }; //IP MALANG
        file "/var/lib/bind/semerua004.pw";
};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153297-29be5e80-26da-11eb-9ec3-ae6add6a7e02.PNG"></p><br>

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

- Ketik `server bind9 stop` pada MALANG untuk testing

<p align="center"><img width="auto" src="https://user-images.githubusercontent.com/61299072/99153325-69854600-26da-11eb-8e1b-932255f62354.PNG"></p><br>


### No. 6
------------------------
**Membuat subdomain dengan alamat http://gunung.semerua04.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.**

- Pada MALANG, edit file **/etc/bind/jarkom/semerua04.pw** seperti dibawah ini

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98790730-b47f2f00-2436-11eb-8a9d-1b15437063c6.png"></p><br>

- Lalu edit file `/etc/bind/named.conf.options` pada MALANG dan tambahkan
```
allow-query{any;};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153569-d3eab600-26db-11eb-896f-e87e26df51fa.PNG"></p><br>

- Kemudian edit file `/etc/bind/named.conf.local` pada MALANG dengan syntax sebagai berikut

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153666-79058e80-26dc-11eb-8613-6d43d8f8e4b4.PNG"></p><br>

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

- Lalu pada MOJOKERTO edit file `/etc/bind/named.conf.options` dan tambahkan
```
allow-query{any;};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153841-b28ac980-26dd-11eb-8c64-2b11e3c79be5.PNG"></p><br>

- Kemudian edit file `/etc/bind/named.conf.local` pada MOJOKERTO seperti berikut

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153871-0695ae00-26de-11eb-8661-0482f050dbce.PNG"></p><br>

- Lalu ketik `mkdir /etc/bind/delegasi` untuk membuat direktori delegasi

- Lalu copy db.local ke direktori delegasi dan beri nama **gunung.semerua04.pw**

```
cp /etc/bind/db.local /etc/bind/delegasi/its.jarkom2020.com
```

- Lalu edit file gunung.semerua04.pw

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98793131-09707480-243a-11eb-8fca-f859955d4031.png"></p><br>

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate

- Testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153902-4a88b300-26de-11eb-950d-6070a0484cdf.png"></p><br>

### No. 7
---------------------------
**Membuat subdomain dengan nama http://naik.gunung.semerua04.pw, dan diarahkan ke IP Server PROBOLINGGO**

Untuk pembuatan subdomain edit file `/etc/bind/jarkom/semerua04.pw` lalu tambahkan konfigurasi seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153996-f9c58a00-26de-11eb-9d4d-6f665fcf72f8.PNG"></p><br>

- Setelah disimpan, lalu service bind9 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99153937-8c195e00-26de-11eb-92da-1feb41dbfc5e.PNG"></p><br>

### No. 8
-----------------------
**Domain http://semerua04.pw memiliki Document Root pada /var/www/semerua04.pw.**

- Masuk ke directory /etc/apache2/sites-available lalu Copy file default menjadi file semerua04.pw pada PROBOLINGGO

- Buka file semerua04.pw

- Tambahkan:
```
ServerName semerua04.pw
ServerAlias www.semerua04.pw
```

- Lalu edit file semerua04.pw menjadi seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154108-ec5ccf80-26df-11eb-8594-0c916eef79d2.png"></p><br>

- Setelah itu ketik `a2ensite semerua04.pw`

- Lalu service apache2 restart

- Lalu pindah ke direktori /var/www, dan download file pendukung dengan perintah
```
wget 10.151.36.202/semeru.pw.zip
```

- Unzip file tersebut dan ubah namanya menjadi semerua04.pw

- Testing pada browser dan ketikkan http://semerua04.pw
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154200-8d4b8a80-26e0-11eb-9467-c99f9deeeb17.PNG"></p><br>

### No. 9
--------------------------
**Mengaktifkan mod rewrite agar urlnya menjadi http://semerua04.pw/home**

- Jalankan perintah `a2enmod rewrite`

- Lalu service apache2 restart
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154306-4c07aa80-26e1-11eb-908a-0bbbe506a207.png"></p><br>

- Masuk ke direktori /var/www/semerua04.pw dan ketikkan `nano .htaccess` dan isi file seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154341-8c672880-26e1-11eb-82bd-1b62207e4144.png"></p><br>

- Lalu pindah ke /etc/apache2/sites-available dan edit file semerua04.pw seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154357-b9b3d680-26e1-11eb-97e6-aabbaa26988b.png"></p><br>

- Lalu service apache2 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154369-d8b26880-26e1-11eb-8fdf-dccbfbfa72c1.png"></p><br>

### No. 10
------------------------
**Web http://penanjakan.semerua04.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semerua04.pw dan memiliki struktur folder seperti yang diminta**

- Masuk ke direktori /etc/apache2/sites-available pada PROBOLINGGO, dan Copy file default menajdi file penanjakan.semerua04.pw

- Edit file penanjakan.semerua04.pw menjadi 
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154459-8291f500-26e2-11eb-80d4-4687214cdf4a.PNG"></p><br>

- Gunakan perintah `a2ensite penanjakan.semerua04.pw`

- Lalu service apache2 restart

- Masuk ke direktori /var/www, dan download file pendukung dengan perintah
```
wget 10.151.36.202/penanjakan.semeru.pw.zip
```

- Unzip file dan ubah namanya menjadi penanjakan.semerua04.pw

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154557-5f1b7a00-26e3-11eb-92a9-38779aeb3707.PNG"></p><br>

### No. 11
**Jika membuka /public maka akan muncul list directory, namun file di dalamnya tidak bisa diakses**

- Masuk ke direktori /etc/apache2/sites-available dan buka file penanjakan.semerua04.pw, lalu edit file tersebut dan tambahkan 
```
 <Directory /var/www/penanjakan.semerua04.pw/public>
     Options +Indexes
 </Directory>
 <Directory /var/www/penanjakan.semerua04.pw/public/javascripts>
     Options -Indexes
 </Directory>
 <Directory /var/www/penanjakan.semerua04.pw/public/css>
     Options -Indexes
 </Directory>
 <Directory /var/www/penanjakan.semerua04.pw/public/images>
     Options -Indexes
 </Directory>
```
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154835-6cd1ff00-26e5-11eb-9f73-35203fee6ad8.PNG"></p><br>

- Lalu service apache2 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154868-a0148e00-26e5-11eb-8e8c-2b25ff7ac469.PNG"></p><br>

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99154869-a1de5180-26e5-11eb-83d6-ef874a2b638b.PNG"></p><br>

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155221-950f2d00-26e8-11eb-87e8-a721a55e55b9.PNG"></p><br>

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155219-93de0000-26e8-11eb-841c-c4e4537ee08d.PNG"></p><br>

### No. 12
-------------------------
**Mengganti error default dari Apache dengan file 404.html**

- Masuk ke direktori /etc/apache2/sites-available, lalu edit file penanjakan.semerua04.pw seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155423-5ed2ad00-26ea-11eb-8654-c6d5795456e6.PNG"></p><br>

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155447-99d4e080-26ea-11eb-9b40-2a0ed80e2538.PNG"></p><br>

### No. 13
--------------------------
**Memperpendek url yang awalnya http://penanjakan.semeruyyy.pw/public/javascripts menjadi http://penanjakan.semeruyyy.pw/js**

- Masuk ke direktori /etc/apache2/sites-available, lalu edit file penanjakan.semerua04.pw dengan menambahkan
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155531-30a19d00-26eb-11eb-8579-d83a37b23e93.png"></p><br>

- Lalu service apache2 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155528-2ed7d980-26eb-11eb-833b-3478cde2720f.png"></p><br>

### No. 14
---------------------------
**Dapat mengakses http://naik.gunung.semerua04.pw:8888**

- Masuk ke direktori /etc/apache2/sites-available, Copy file default menjadi file naik.gunung.semerua04.pw, dan edit file tersebut menjadi
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155574-b32a5c80-26eb-11eb-9b89-9d86ed0cc14a.PNG"></p><br>

- Lalu pindah ke direktori /etc/apache2 dan edit file ports.conf
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155589-e2d96480-26eb-11eb-8eb6-389c15371d52.PNG"></p><br>

- Jalankan perintah `a2ensite naik.gunung.semerua04.pw`

- Lalu service apache2 restart

- Masuk ke direktori /var/www, dan download file pendukung dengan perintah
```
wget 10.151.36.202/naik.gunung.semeru.pw.zip
```

- Unzip file tersebut

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155649-62673380-26ec-11eb-9410-8def534867f6.PNG"></p><br>

### No. 15
--------------------------
**Buat username dan password saat mengakses web**

- Install apache utilities package dengan 
```
apt-get update
apt-get install apache2 apache2-utils
```

- Lalu buat file password, dan masukkan username dan password
```
htpasswd -c /etc/apache2/.htpasswd semeru
```

- Lalu edit file pada /etc/apache2/sites-enabled/naik.gunung.semerua04.pw seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155725-17015500-26ed-11eb-9285-b3797abfcff8.PNG"></p><br>

- Lalu service apache2 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155724-15379180-26ed-11eb-828c-27527f92827f.PNG"></p><br>

### No. 16
------------------------------
**Jika membuka IP PROBOLINGGO akan langusng diarahkan ke http://semerua04.pw**

- Masuk ke direktori /var/www dan buat file .htaccess seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155775-94c56080-26ed-11eb-9239-c0c8c29d894c.PNG"></p><br>

- Lalu service apache2 restart

- Lakukan testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155803-e66deb00-26ed-11eb-88ec-e33525c2174a.PNG"></p><br>

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155806-ec63cc00-26ed-11eb-8f75-1a879ecb7980.PNG"></p><br>

### No. 17
-----------------------
**Jika membuka semua image yang mengandung kata semeru maka akan dialihkan ke semeru.jpg**

- Masuk ke direktori /var/www/penanjakan.semerua04.pw dan buat file .htaccess seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155856-58decb00-26ee-11eb-93fe-46660fc2f52b.PNG"></p><br>

- Lalu service apache2 restart

- Lakukan testing dengan menginputkan penanjakan.semerua04.pw/public/images/lalalasemeru.jpg 
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155857-59776180-26ee-11eb-9371-5af836a43313.PNG"></p><br>

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/99155959-76f8fb00-26ef-11eb-9630-27a603845498.PNG"></p><br>





