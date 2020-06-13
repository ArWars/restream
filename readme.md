# Sistema de restream

Este sistema esta creado para poder restremear desde tu OBS a twitch, facebook, youtube, 

### Requisitos
* Ubuntu >= 16.04 

### Caracteristicas
* Administre sus Lineas(Clientes), **cree**, **extienda**, **finalice** a sus clientes. 
### Instalación Automatica del Panel

<details><summary><b>Como Instalar?</b></summary>

1. Copie y pege en la consola

    ```sh
    apt-get install -y libpcre3 libpcre3-dev make gcc libssl-dev libnginx-mod-rtmp
    cd ~
    wget http://nginx.org/download/nginx-1.12.2.tar.gz
    wget https://github.com/arut/nginx-rtmp-module/archive/master.tar.gz
    tar -xzvf nginx-1.12.2.tar.gz
    tar -xzvf master.tar.gz
    rm nginx-1.12.2.tar.gz
    rm master.tar.gz
    cd nginx-1.12.2
    ./configure --with-http_ssl_module --without-http_gzip_module --add-module=../nginx-rtmp-module-master --with-http_secure_link_module --with-http_v2_module
    make && make install
    cd /usr/local/nginx
    ls
    wget https://raw.githubusercontent.com/JasonGiedymin/nginx-init-ubuntu/master/nginx -O /etc/init.d/nginx
    chmod +x /etc/init.d/nginx
    update-rc.d nginx defaults 
    apt-get install -y software-properties-common 
    apt-get install -y ffmpeg
    sudo apt-add-repository ppa:jon-severinsson/ffmpeg
    apt-get update
    apt-get install -y curl
    wget https://raw.githubusercontent.com/AriieelEsteban/restream/master/nginx.conf -O /usr/local/nginx/conf/nginx.conf
    chown -R www-data:www-data /usr/local/nginx/html
    sudo apt-get install stunnel4 -y
    wget https://raw.githubusercontent.com/AriieelEsteban/restream/master/stunnel.conf -O /etc/stunnel/stunnel.conf
    ```
    
2.  Modificar ENABLE=0 a ENABLE=1
    ```
      sudo nano /etc/default/stunnel4
      sudo systemctl enable stunnel4.service
      sudo systemctl restart stunnel4.service
    ```
3. Modificar las KEY de Twitch, etc, quitar el # en los push que ahi en la aplicación de /live
    ``` 
      nano /usr/local/nginx/conf/nginx.conf
    ```
