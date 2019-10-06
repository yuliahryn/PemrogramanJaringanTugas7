## Anggota Kelompok :
- Aditya Eka Bagaskara (1301164222)
- Ilham Ibnu Purnomo (1301164089)
- Adisca Naufal Ristanto (1301164358)


## Finite State Machine

Pada tugas 7 ini, kami meneruskan aplikasi web server yang sudah kami buat pada tugas 6 dengan menambahkan fitur serve koneksi HTTPS. Perbedaannya, request yang dikirim oleh client ke server akan dienkripsi terlebih dahulu, response yang dikirim oleh server ke client dienkripsi juga.

![fsm](https://raw.githubusercontent.com/adityaeka26/network-programming-7/master/fsm.png)


## Web Server HTTPS with Config


Untuk membuat web server yang dapat melakukan serve koneksi HTTPS, hal yang pertama kami lakukan adalah men-generate private key dan public key. 

Private key dan public key dapat di-generate dengan menggunakan aplikasi openssl dengan cara :

````
openssl genrsa -out server.key 2048
openssl ecparam -genkey -name secp384r1 -out server.key
openssl req -new -x509 -sha256 -key server.key -out server.crt -days 3650
````

Pada saat mengeksekusi command terakhir, akan disuruh untuk memasukkan beberapa informasi. Pastikan informasi yang diinput benar.

![generate-key](https://raw.githubusercontent.com/adityaeka26/network-programming-7/master/screenshots/generate-key.png)

Setelah mengeksekusi ketiga command di atas, maka akan muncul 2 file, yaitu server.crt dan server.key. Pindah kedua file tersebut ke dalam folder web server yang akan dibuat.

Maka web server yang tadinya hanya menggunakan HTTP kini dapat melakukan serve untuk koneksi HTTPS (dapat dilihat dari alamat web yang menjadi https://localhost) yang tentunya membuat web server menjadi lebih aman.

![web-server-https](https://raw.githubusercontent.com/adityaeka26/network-programming-7/master/screenshots/web-server-ssl.png)

