1.  Instalar:		
		sudo apt-get install build-essential git-core libssl-dev libssl0.9.8 
2. 	Clonar el repositorio:		
		git clone git://github.com/joyent/node
3.	Ubicarce en la carpeta del repositorio clonado:  
		cd node 
4. 	Pasar Nodejs a la ultima version estable (0.8.4): 		
		git checkout v0.8.4
5.  Compilar e instalar NodeJs:		
	*	./configure
	*	make
	*	sudo make install
6. 	Generar archivo package.json en el directorio donde se creará el proyecto		
		{     
			"name": "miProyecto",    
			"version": "0.0.1",     
			"dependencies": {         
				"express"     : "*", 
				"consolidate" : "*",      
				"socket.io"   : "*",
				"swig"        : "*"    
			} 
		} 
7. 	Instalar paquetes		
		npm install		
	Si hay problemas con certificado SSL cambiar la siguiente configuracion		
		npm config set registry="http://registry.npmjs.org/"
8.  Ver versiones instaladas y reemplazarlas en el archivo package.json 		
			npm list
9.  Lanzar aplicación sin necesidad de tener la consola abierta	

	sudo npm install -g forever 				Instalar forever		
	forever start -l server.log server.js		Lanzar aplicación		
	tail -f ~/.forever/server.log				Ver el log
	forever stop -l server.log server.js		Detener la apliación
	
