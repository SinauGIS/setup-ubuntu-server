# Install Tomcat di Ubuntu

1. Buat user tomcat dengan command    
`sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat`   

2. Install unzip dan wget dengan command   
`sudo apt install unzip wget`   

3. Masuk ke direktori tmp kemudian download tomcat 9 dengan command   
`cd /tmp`   
`wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.75/ bin/apache-tomcat-9.0.75.zip`   

4. Setelah selesai download tomcat 9 lakukan unzip dengan command   
`unzip apache-tomcat-9.0.75.zip`   

5. Pindahkan tomcat 9 ke direktori /opt/tomcat dengan command   
`sudo mkdir -p /opt/tomcat`   
`sudo mv apache-tomcat-9.0.75 /opt/tomcat/`   

6. Buat symlink tomcat 9  dengan command   
`sudo ln -s /opt/tomcat/apache-tomcat-9.0.75 /opt/tomcat/latest`   

7. Ubah direktori /opt/tomcat menjadi kepemilikan user dan grup tomcat dengan command   
`sudo chown -R tomcat: /opt/tomcat`   

8. Jadikan script di dalam direktori bin dapat dieksekusi dengan command   
`sudo sh -c 'chmod +x /opt/tomcat/latest/bin/*.sh'`   

9. Buat file unit systemd   
`sudo nano /etc/systemd/system/tomcat.service`   

10. Isikan di dalam file tomcat.service tersebut dengan script berikut   
`[Unit]`   
`Description=Tomcat 9 servlet container`   
`After=network.target`   
` `   
`[Service]`   
`Type=forking`   
` `   
`User=tomcat`   
`Group=tomcat`   
` `   
`Environment="JAVA_HOME=/usr/lib/jvm/java-1.17.0-openjdk-amd64"`   
`Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"`   
` `   
`Environment="CATALINA_BASE=/opt/tomcat/latest"`   
`Environment="CATALINA_HOME=/opt/tomcat/latest"`   
`Environment="CATALINA_PID=/opt/tomcat/latest/temp/tomcat.pid"`   
`Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"`   
` `   
`ExecStart=/opt/tomcat/latest/bin/startup.sh`   
`ExecStop=/opt/tomcat/latest/bin/shutdown.sh`   
` `   
`[Install]`   
`WantedBy=multi-user.target`   

11. Restart daemon dengan command   
`sudo systemctl daemon-reload`   

12. Start tomcat dengan command   
`sudo systemctl start tomcat`

13. Untuk melihat status service tomcat gunakan command   
`sudo systemctl status tomcat`   

14. Jika status service tomcat sudah aktif, cobalah akses melalui browser client untuk mengakses tomcat dengan ip/domain server pada port 8080
