# Install PostGIS di Ubuntu

1. Install PostGIS   
`sudo apt update`   
`sudo apt install postgis`   

2. Ketikkan <b>Y</b> untuk melanjutkan instalasi dan tunggu hingga proses install selesai.   

3. Masuk ke dalam postgresql dengan command   
`sudo -u postgres psql`   

4. Koneksikan dengan database dataspasial yang telah dibuat dengan command   
`\c dataspasial`   

5. Tambahkan extensi postgis ke dalam database dataspasial dengan command   
`CREATE EXTENSION postgis;`   

6. Untuk melihat extensi yang terinstal di database gunakan command berikut   
`\dx`
