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

	sudo apt-get install php5-mongo
