* Instalar		
	sudo npm install stylus -g
	sudo npm install nib -g
* Compilar archivo (compila dentro de la carpeta css, y se actualiza cada vez que se actualiza el archivo .styl)		
	stylus -c -w -o css/ stylus/archivo.styl
* Instalar nib		
	sudo npm install nib -g
* Compiar con nib		
	stylus -u nib -c -w -o css/ stylus/archivo.styl
* Compiar css a stylus		
 	 stylus -C css/archivo.css stylus/archivo.styl
* Instalar css2stylus		
	sudo npm install -g css2stylus
* Convertir archivo css a stylus		
	css2stylus archivo.css
	
