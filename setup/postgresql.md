# Install & Konfigurasi PostgreSQL di Ubuntu

___   

## Install PostgreSQL

1. Install postgresql   
`sudo apt update`   
`sudo apt install postgresql postgresql-contrib`   

2. Masuk dengan user <b>postgres</b>, ketikkan command berikut   
`sudo -u postgres psql`   

3. Untuk membuat database misal dengan nama dataspasial, ketikkan command berikut   
`CREATE DATABASE dataspasial;`   

4. Untuk melihat list database gunakan command   
`\l`   

5. Untuk mengubah password gunakan command   
`\password`   

6. Untuk keluar gunakan command   
`\q`   

___   

## Konfigurasi PostgreSQL

1. Masuk ke direktori /etc/postgresql/14/main melalui command
`cd /etc/postgresql/14/main`   

2. Buka <b>pg_hba.conf</b> menggunakan nano dengan command berikut
`sudo nano pg_hba.conf`   

3. Tambahkan konfigurasi berikut ini pada # IPv4 local connections:  
`host     all     all     0.0.0.0/0     md5`   

4. Simpan dengan menggunakan <b>Ctrl + X</b>   
5. Buka <b>postgresql.conf</b> menggunakan nano dengan command berikut   
`sudo nano postgresql.conf`   

6. Ubah baris berikut   
`listen_addresses = 'localhost'`   
menjadi   
`listen_addresses = '*'`   

7. Simpan dengan menggunakan <b>Ctrl + X</b>

8. jalankan perintah   
`sudo systemctl restart postgresql`   