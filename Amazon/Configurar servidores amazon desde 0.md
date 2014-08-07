CONFIGURACION DE SERVIDORES AMAZON DESDE 0


Este documento es un paso a paso de como configurar las diferentes instancias de AWS para una aplicación PHP y MySQL sobre un servidor Ubuntu. Las configuraciones se realizaran para un servidor web (instancia EC2), un servidor de base de datos (instancia RDS) y un servidor de correo (SES).



Crear instancia EC2
===================

Creación
--------
* Ingresar a EC2
* Seleccionar la región donde se creará la instancia (ej. N. virgina)
* Ingresar a launch instance
* Seleccionar el sistema operativo (ej. ubuntu server)
* Seleccionar el tipo de instancia (ej. micro - porque hace parte de la capa gratuita)
* Configurar la instancia 
* Asignar tamaño de volumen storage
* Crear y asignar grupo de seguridad para la instancia
	* Agregar las siguientes reglas al grupo de seguridad
		* SSH con puerto 22 con acceso a la ip del equipo de desarrollo (My IP)
		* HTTP con puerto 80 con acceso a toda ip (Anywhere)
* Lanzar la instancia
* Crear una key pary en el modalbox que aparece
* Descargar y guardar en un lugar seguro el archivo .pem (Esta es la llave de acceso al servidor)
* Finalizar 

Conexión con la instancia
-------------------------
* Seleccionar la insancia en la lista de instancias
* Dar nombre a la instancia
* Crear Eslastic IP y asignarla a la instancia
* Verificar en los detalles que la instancia tenga una ip publica y/o elastic ip
* Ir a Connect (Aca se mostrará como conectarse a la instancia de diferentes formas)
* Dar permisos de solo lectura a la key pair
	chmod 400 my_key_pair.pem
* En la consola ingresar la siguiente linea:
	ssh -i my_key_pair.pem ubuntu@<elastic_ip>
* Se preguntará si desea agregar a la lista de host seguros, damos yes
* En este momento ya se debe estar conectado al servidor


Configuración inicial del servidor
----------------------------------

* Instalar lamp server

	* sudo apt-get install tasksel
	* sudo aptitude update
	* sudo tasksel
	* Seleccionar lampp server con la tecla espacio y aceptar
	* Comprobar funcionamiento ingresando la ip en el navegador
	* Instalar las siguientes extensiones de php
		* sudo apt-get install php5-dev
		* sudo apt-get install php-pear
		* sudo apt-get install php5-json
		* sudo apt-get install php5-curl
		* sudo apt-get install php5-intl
		* sudo apt-get install php5-gd
		* sudo apt-get install php-apc
			* agregar lineas a php.ini (No es necesario en las ultimas versiones de apache)
				extension=apc.so
				apc.apc.stat = 0
				apc.include_once_override = 1
				apc.shm_size = 64M
	* habilitar mod_rewrite (En la configuración por defecto de apache está deshabilitado)
		sudo a2enmod rewrite
	* Reiniciar apache (sudo service apache2 restart)

* Instalar GIT
	* sudo apt-get install git-core


Creacion de volumen EBS para almacenamiento 
-------------------------------------------
(https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html)

* Crear volumen EBS en la misma zona de la instancia EC2
	* especificar el nombre del dispositivo /dev/sdf (default)
* Seleccione el volumen creado y seleccione attach volumen y seleccione la instancia EC2
* Conectarce a la instancia con ssh
* ejecutar la siguiente linea para ver los volumenes adjunatos a la instancia 
	* lsblk
	* deben aparecer 2 volumenes root y el volumen que creamos (para el que el MOUNTPOINT aparece como / es root, el otro es el recien creado) 
	* Verificar el nombre del volumen que creamos (xvdf en caso de ubuntu)
	* Con este nombre ya sabemos que el volumen esta montado en /dev/xvdf (la salida de lsblk quita el prefijo /dev por ello debemos tenerla en cuenta)
* Dar formato al volumen
	* Verificar el file system con la linea: sudo file -s /dev/xvdf
	* Si el resultado es "data" ejecutar la siguiente linea (en otro caso no es necesario y puede borrar la información que exista):
		* sudo mkfs -t ext4 /dev/xvdf
* Crear punto de montaje (ubicación de acceso a través del sistema de archivos)
	* sudo mkdir /vol (crear carpeta donde se montará el volumen)
	* sudo mount /dev/xvdf /vol (Montar volumen en la carpeta)
	* Agregar volumen al archivo de arranque del sistema
		* Crear copia de seguridad:
			sudo cp /etc/fstab /etc/fstab.orig
		* Abrir archivo
			sudo vim /etc/fstab
		* Agregar la siguiente linea al final del archivo
			/dev/xvdf /vol ext4 defaults 0 2
		* Guardar cambios
		* Verificar que no hallan errores (si hay errores deben corregirse o si no el sistema puede no arrancar cuando se apague)
			sudo mount -a


Configurar Host
---------------
* Crear copia de seguridad del sitio por defecto de apache
	sudo cp /etc/apache2/sites-availables/000-default.conf /etc/apache2/sites-available/000-default.orig.conf
* Abrir archivo
	sudo vim /etc/apache2/sites-availables/000-default.conf
* Agregar 
	ServerName midominio.com (o localhost para acceder con la ip unicamente)
* Editar la dirección de correo en ServerAdmin
* Editar DocumentRoot
	DocumentRoot /vol (si el proyecto se encuentra en otra carpeta dentro de /vol se puede indicar la ruta completa)
* Reemplazar:
	<Directory /var/www/>
	por
	<Directory /vol/> (si el proyecto se encuentra en otra carpeta dentro de /vol se puede indicar la ruta completa)
* Agregar ServerName en /etc/apache2/apache2.conf
	ServerName localhost (o el dominio)
* sudo service apache2 restart




Crear instancia RDS
===================

* Launch DB Instance
* Seleccionar MySQL
* No usar Multi-AZ Deployment (seleccinarlo puede generar costos adicionales)
* Seleccionar la version 5.5.31 (5.6.x no soporta current_timestamp)
* Seleccionar tipo de instancia micro
* Seleccionar 5GB en allocated storage
* Ingresar los identificadores para acceder a la base de datos
	DB Instance Identifier
	Master Username
	Master Password
* Ingresar el nombre de la base de datos y dejar los demas datos por defecto
* Seleccionar el mismo grupo de seguridad de la instancia EC2
* Programar backups 
* Lanzar instancia
* Agregar el permiso para mysql al grupo de seguridad que se selecciono
	* Hacer click sobre el nombre del grupo en los detalles de la instancia EC2
	* Seleccionar el grupo e ir a la pestaña inbound 
	* Seleccionar MYSQL y escoger las ip de acceso (0.0.0.0/0 es acceso desde cualquier ip)
* Para conectarse al servidor de base de datos se usa el endpoint de la instancia y el usuario y contraseña que se registraron en la creación



Configurar SES
==============
* Ir a SMTP Settings y dar click en "Create My SMTP Credentials"
* Crear usuario (IAM) para uso de SES
* Descargar las credenciales (Estas credenciales no se pueden consultar despues, si se pierden debera crearse un nuevo IAM)
* Ir a Email Addresses y agregar un correo real desde donde se realizarán los envíos en la aplicación
* Pueden enviarse correos de prueba entre las direcciones de correo registradas
* Para poder usar SES en producción debe enviarse la peticion de acceso a producción
	* Click en Request Production Access
	* Seleccionar Service Limit Increase
	* Seleccionar SES Production Access
	* Seleccionar la region 
	* Marcar todas las opciones en Pre-Production Checklist
	* Ingresar una descripción de solicitud de apertura del servicio en ingles
	* Ingresar la información solicitada del administrador de la cuenta Amazon
* Para conectarse al servidor se usa el ServerName y el Username y Password del archivo descargado
