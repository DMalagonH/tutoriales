# Configuración de Ubuntu Server 16

## Instalación de LAMPP y extensiones

### Apache
* `sudo apt-get install apache2`
* `sudo systemctl enable apache2`
* `sudo systemctl start apache2`
* `sudo systemctl status apache2`

### MySQL 
* `sudo apt-get install mysql-server mysql-client`
* `sudo systemctl status mysql`

### PHP 5 y 7
* `sudo add-apt-repository ppa:ondrej/php`
* `sudo apt-get update`
* `sudo get install php7.0 php5.6 php5.6-mysql php-gettext php5.6-mbstring php-xdebug libapache2-mod-php5.6 libapache2-mod-php7.0`

#### Cambiar de PHP 5 a 7
* sudo a2dismod php5.6
* sudo a2enmod php7.0
* sudo service apache2 restart
* sudo ln -sfn /usr/bin/php7.0 /etc/alternatives/php
* php -v

#### Cambiar de PHP 7 a 5
* sudo a2dismod php7.0; sudo a2enmod php5.6;
* sudo a2enmod php5.6
* sudo service apache2 restart
* sudo ln -sfn /usr/bin/php7.0 /etc/alternatives/php
* php -v 

#### Extensiones PHP 5

* PHP-DEV: `sudo apt-get install php5.6-dev`
* PEAR: `sudo apt-get install php-pear`
* JSON: `sudo apt-get install php5.6-json`
* cURL: `sudo apt-get install php5.6-curl`
* intl: `sudo apt-get install php5.6-intl`
* imagick: `sudo apt-get install php5.6-imagick --fix-missing` (para funciones relacionadas a imagenes)
* APC: `sudo apt-get install php5.6-apc`
* Mongo `sudo apt-get install php5.6-mongo --fix-missing`
* Redis `sudo apt-get install php5.6-redis`

## cURL
`sudo apt-get install curl`

## GIT
`sudo apt-get install git-core`

## NodeJS 4 [Fuente](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)

* `curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -`
* `sudo apt-get install -y nodejs`

#### Módulos globales
* `sudo npm -g install forever`
*  sudo npm -g install forever-service
* `sudo npm -g install grunt`

## MongoDB [Fuente](https://www.linode.com/docs/databases/mongodb/install-mongodb-on-ubuntu-16-04)

* `sudo apt-get update && sudo apt-get upgrade`
* `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927`
* `echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`
* `sudo apt-get update`
* `sudo apt-get install -y mongodb-org`

## Redis [Fuente](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)

* `sudo apt-get install build-essential`
* `sudo apt-get install tcl8.5`
* `wget http://download.redis.io/releases/redis-stable.tar.gz`
* `tar xzf redis-stable.tar.gz`
* `cd redis-stable`
* `make`
* `make test`
* `sudo make install`
* `cd utils`
* `sudo ./install_server.sh`

## wkhtmltox (html a pdf y jpg)
#### Instalar
* `sudo add-apt-repository ppa:ecometrica/servers`
* `sudo apt-get update`
* `sudo apt-get install wkhtmltopdf`  

#### Descagar paquete
* `wget http://download.gna.org/wkhtmltopdf/0.12/0.12.3/wkhtmltox-0.12.3_linux-generic-amd64.tar.xz` ([Obtener url](http://wkhtmltopdf.org/downloads.html))
* `tar Jxvf wkhtmltox-0.12.3_linux-generic-amd64.tar.xz`
* `sudo cp -R wkhtmltox /usr/local/bin/wkhtmltox`

