# Install & Konfigurasi GeoServer Tomcat di Ubuntu

___   
## Install GeoServer Tomcat

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

___   

## Mengaktifkan Layer JSONP

1. buka file <b>web.xml</b> dari geoserver   
```sudo nano /opt/tomcat/latest/webapps/geoserver/WEB-INF/web.xml```

2. Uncomment following filter to enable JSONP in Tomcat. Do not forget the second config block further down   
  ```
  <context-param>
    <param-name>ENABLE_JSONP</param-name>
    <param-value>true</param-value>
  </context-param>
  ```

___   

## Enable CORS Origin Filter

1. buka file <b>web.xml</b> dari geoserver   
```sudo nano /opt/tomcat/latest/webapps/geoserver/WEB-INF/web.xml```   

2. Uncomment following filter to enable CORS in Tomcat. Do not forget the second config block further down.   
```
<filter>
    <filter-name>CorsFilter</filter-name>
    <filter-class>org.apache.catalina.filters.CorsFilter</filter-class>
    <init-param>
        <param-name>cors.allowed.origins</param-name>
        <param-value>*</param-value>
    </init-param>
    <init-param>
        <param-name>cors.allowed.methods</param-name>
        <param-value>GET,POST,HEAD,OPTIONS,PUT</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>CorsFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

3. Uncomment following filter to enable CORS    
```
  <filter-mapping>
    <filter-name>cross-origin</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>
```