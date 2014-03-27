Instalación del motor
=====================

Link: http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/


* Importar clave publica de mongo para ubuntu		
	sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

* Ejecutar el siguiente comando para crear un archivo de mongoDB		
	echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list

* Actualizar apt		
	sudo apt-get update

* Instalar mongodb		
	sudo apt-get install mongodb-10gen

* Iniciar mongodb		
	sudo service mongodb start

* Detener mongodb		
	sudo service mongodb stop

* Restart mongodb		
	sudo service mongodb restart


Comandos básicos de mongo en CLI
--------------------------------
	
	mongo 						Conectar con mongodb
	db 							Ver db en uso
	show dbs					Ver listado de bases de datos
	use mydb					Crear y/o usar una base de datos
	db.mydb.find()				Muestra la colección
	db.mydb.save({key:value})	Guarda el objeto {key:value} en la colección



Extensión para PHP
==================

Link: http://www.tecnopedia.net/mongodb/tutorial-instalar-mongodb-en-ubuntu/

* Verificar que la extensión no este instalada		
	php --re mongo

* Instalar extensión		
	sudo pecl install mongo	

* Agregar la siguiente linea al php.ini (/etc/php5/apache2/php.ini Y /etc/php5/cli/php.ini)		
	extension=mongo.so

* Reiniciar apache		
	sudo service apache2 restart

	