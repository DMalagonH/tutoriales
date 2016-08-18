# Configuración de Ubuntu Server 14

## Instalación de LAMPP y extensiones

* `sudo apt-get install tasksel`
* `sudo tasksel`
* Seleccionar lampp server usando la tecla espacio
* Enter

#### Extensiones PHP 5

* PHP-DEV: `sudo apt-get install php5-dev`
* PEAR: `sudo apt-get install php-pear`
* JSON: `sudo apt-get install php5-json`
* cURL: `sudo apt-get install php5-curl`
* intl: `sudo apt-get install php5-intl`
* gd: `sudo apt-get install php5-gd` (para funciones relacionadas a imagenes)
* imagick: `sudo apt-get install php5-imagick` (para funciones relacionadas a imagenes)
* APC: `sudo apt-get install php-apc`
* Mongo `sudo apt-get install php5-mongo`
* Redis `sudo apt-get install php5-redis`

## cURL
`sudo apt-get install curl`

## GIT
`sudo apt-get install git-core`

## NodeJS 4 [Fuente](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)

* `curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -`
* `sudo apt-get install -y nodejs`

#### Módulos globales
* `sudo npm -g install forever`
* `sudo npm -g install grunt`

## MongoDB [Fuente](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-14-04)

* `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10`
* `echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list`
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
