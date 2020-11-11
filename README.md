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

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98789714-3e2dfd00-2435-11eb-9539-0d8b0c072d13.png"></p><br>

### No. 6
------------------------
**Membuat subdomain dengan alamat http://gunung.semerua04.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.**

- Pada MALANG, edit file **/etc/bind/jarkom/semerua04.pw** seperti dibawah ini

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98790730-b47f2f00-2436-11eb-8a9d-1b15437063c6.png"></p><br>

- Lalu edit file `/etc/bind/named.conf.options` pada MALANG.

- Kemudian edit file `/etc/bind/named.conf.local` dengan syntax sebagai berikut

```
zone "semerua04.pw" {
    type master;
    file "/etc/bind/jarkom/semerua04.pw";
    allow-transfer { 10.151.73.43; }; //IP MOJOKERTO
};
```

<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98791381-9108b400-2437-11eb-9a06-213e5b019619.png"></p><br>
- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate 

- Lalu pada MOJOKERTO edit file `/etc/bind/named.conf.options`


- Setelah itu pada MOJOKERTO edit file **/etc/bind/named.conf.local** seperti berikut
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98791728-0d02fc00-2438-11eb-9d1d-2f17cce3ee78.png"></p><br>

- Lalu ketik `mkdir /etc/bind/delegasi` untuk membuat direktori delegasi
- Lalu copy db.local ke direktori delegasi dan beri nama **gunung.semerua04.pw**

```
cp /etc/bind/db.local /etc/bind/delegasi/its.jarkom2020.com
```

- Lalu edit file gunung.semerua04.pw
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98793131-09707480-243a-11eb-8fca-f859955d4031.png"></p><br>

- Setelah disimpan, lalu ketik service bind9 restart pada uml untuk mengupdate

- Testing
<p align="center"><img width="500" src="https://user-images.githubusercontent.com/61299072/98794216-5c96f700-243b-11eb-9e58-f750f6ce3d05.png"></p><br>

### No. 7
---------------------------
**Membuat subdomain dengan nama http://naik.gunung.semerua04.pw, dan diarahkan ke IP Server PROBOLINGGO**

Untuk pembuatan subdomain edit file `/etc/bind/jarkom/semerua04.pw` lalu tambahkan konfigurasi seperti berikut. Setelah disimpan, lalu 
service bind9 restart dan lakukan testing pada klien
<p align="center"><img width="auto" src="https://user-images.githubusercontent.com/61299072/98797349-03c95d80-243f-11eb-9fd8-8cfd043fa120.png"></p><br>

