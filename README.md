# docker-images-armv7

THIS REPO IS NO LONGER UPDATED.

## Pull

    $ docker pull adann0/certbot:armv7
    $ docker pull adann0/mariadb:armv7
    $ docker pull adann0/samba-ldap:armv7
    $ docker pull adann0/openldap:armv7
    $ docker pull adann0/phpldapadmin:armv7
    $ docker pull adann0/nginx-ldap-auth-daemon:armv7

## Build

### Enable Docker Experimental Features

Client :

    $ cd
    $ nano .docker/config.json # ,"experimental":"enabled"

Server :

    $ echo {"experimental":true} >> /etc/docker/daemon.json

### Certbot

Just build the image on the Raspberry :

    $ git clone https://github.com/certbot/certbot.git &&
    cd certbot &&
    docker build -t "certbot:armv7" .

### Adminer

    $ git clone https://github.com/TimWolla/docker-adminer.git &&
    cd docker-adminer/4 &&
    docker build -t "adminer:armv7" .

### Nginx-LDAP-Auth-Daemon

    $ git clone https://github.com/nginxinc/nginx-ldap-auth.git &&
    cd nginx-ldap-auth &&
    docker build -t "nginx-ldap-auth-daemon:armv7" .

### OpenLDAP + phpLDAPadmin

   https://github.com/adann0/openldap-armv7

### MariaDB

   https://github.com/adann0/mariadb-armv7

### Samba-LDAP

   https://github.com/adann0/samba-ldap-armv7

### Push

To push Images on Docker Hub :

    $ docker login --username=<hub_repo> --email=<hub_email>
    $ docker images
    $ docker tag <image_id> <hub_repo>/<image>:<tag>
    $ docker push <hub_repo>/<image>:<tag>

Then :

    $ docker manifest inspect --verbose <hub_repo>/<image>:<tag> # => Architecture : arm
    $ docker pull <hub_repo>/<image>:<tag>
