# CATATAN SAKTI UNTUK MENGKONVERT MYSQL KE POSTGRESQL UNTUK HEROKU

Heroku adalah sebuah layanan dimana kita dapat menghosting aplikasi web kita. heroku tidak seperti layanan hosting lainnya, heroku menggunaka sistem push untuk mengupload file ke heroku.
Untuk heroku versi gratis atau free hanya memberikan layanan menggunakan database postgresql.
catatan ini dibuat untuk melakukan konversi database dari mysql ke postgresql yang nantinya akan di upload ke heroku

## BERIKUT CARA MELAKUKAN KONVERSI KE DARI MYSQL KE POSTGRESQL
Pertama tama kunjungi link berikut dan dowload isi dari repository berikut.
```bash
https://github.com/lanyrd/mysql-postgresql-converter
```
kemudian kita ekstrak dulu database dari mysql dengan syntax berikut dalam terminal
```bash
sudo mysqldump --compatible=postgresql --default-character-set=utf8 -r nama_database.mysql -u root -p nama_database
```
setelah itu lakukan konversi hasik ekstral .mysql ke extensi .psql dengan menggunakan aplikasi yang kita download sebelumnya
```bash
python db_converter.py skripsi.mysql skripsi.psql
```

## IMPORT DATA KE POSTGRESQL
Sebelum kita gunakan ke heroku, maka kita harus melakukan hal hal tertentu sesuai dengan aturan dari heroku. disini saya akan memberikan dua cara.
tapi sebelum itu kita import dulu database yang sudah kita konversi ke dalam database postgresql.
bagi yang belum menginstall postgresql, silahkan buka catatan sakti [POSTGRESQL](
https://github.com/masariuman/catatan_sakti/blob/master/postgresql_ubuntu_18.04(current).md) .

### MEMBUAT DATABASE
Setelah melakukan installasi dan setting pada postgresql, maka kita lakukan import data yang sudah kita konversi tadi kedalam postgresql.
pertama-tama kita harus membuat database terlebih dahulu dengan syntax berikut
```bash
sudo -u postgres createdb nama_database
```

### IMPORT DATA
Setelah itu kita dapat melakukan import data kedalam database dengan syntax berikut
```bash
sudo -u postgres psql -d nama_database -f nama_database.psql
```
Kemudian kita dapat mengecek apakah data sudah masuk atau belum dengan syntax berikut
- Masuk kedalam PostgreSQL
```bash
sudo -u postgres psql
```
- Mengecek Database
```bash
\d
```
- Memilih Database Yang Akan Dicek
```bash
\c nama_database
```
- Mengecek Tabel Pada Database
```bash
\d
```
- Mengecek Value dari Tabel
```bash
TABLE ****
```

# SELAMAT !!! ANDA SUDAH BERHASIL IMPORT DATA KE DALAM DATABASE POSTGRESQL

## UNTUK MELAKUKAN IMPORT DATABASE DARI POSTGRESQL LOKAL KE HEROKU, SILAHKAN LIHAT PADA CATATAN [IMPORT DATABASE KE HEROKU]()
