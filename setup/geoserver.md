# Install GeoServer Tomcat di Ubuntu

1. Masuk ke direktori /tmp kemudian download GeoServer    
`cd /tmp`   
`wget https://sourceforge.net/projects/geoserver/files/GeoServer/2.23.0/geoserver-2.23.0-war.zip`   

2. Unzip geoserver dan pindahkan ke direktori webapps tomcat   
`unzip geoserver-2.23.0-war.zip`   
`sudo mv geoserver.war /opt/tomcat/latest/webapps`   

3. Jalankan geoserver melalui browser client dengan url   
[NAMA_DOMAIN / IP_ADDRESS]:8080/geoserver   
Misalnya   
localhost:8080/geoserver   


