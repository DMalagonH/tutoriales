# Instalación de Apache Cordova en Ubuntu

## Instalar Java
`sudo apt-get install openjdk-8-jdk ant`

## Instalar SDK Android
1. [Descargar SDK para linux](https://developer.android.com/studio/index.html?hl=es-419)
2. Descomprimir
3. Crear una carpeta en el directorio del usuario con el nombre "android-sdk" (o cualquier otro nombre) y copiar dentro la carpeta tools sin cambiar su nombre.
3. Agregar SDK al path del sistema  
	`export PATH=${PATH}:/home/{usuario}/android-sdk/tools/`
4. Abrir Android SDK Manager con el comando:  
	`android`
5. Instalar paquetes del SDK para las versiones de Android necesarias