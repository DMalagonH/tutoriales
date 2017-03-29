# Instalación de Apache Cordova en Ubuntu

## Instalar Java Oracle JDK [Ver fuente](http://tutorialforlinux.com/how-to-install-oracle-jdk-8-on-ubuntu-linux-distro-easy-guide/)
* `tar xvzf ~/Downloads/jdk-8*.tar.gz -C /tmp/`
* `sudo su`
* `if [ ! -d "/usr/lib/jvm" ]; then mkdir /usr/lib/jvm; fi`
* `chown -R root:root /tmp/jdk1.8*`
* `chmod -R +x /tmp/jdk1.8*/bin`
* `mv /tmp/jdk1.8* /usr/lib/jvm/`
* `update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8*/bin/java 1065`
* `update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8*/bin/javac 1065`
* `update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk1.8*/bin/jar 1065`
* `update-alternatives --install /usr/bin/javaws javaws /usr/lib/jvm/jdk1.8*/bin/javaws 1065`
* Seleccionar versión de JDK ingresando el número de la primera columna de la lista de versiones  
`update-alternatives --config java`


## Instalar SDK Android [Ver Fuente](http://tutorialforlinux.com/2016/03/27/how-to-install-android-sdk-tools-on-ubuntu-16-04-xenial-32-64bit/)
* [Descargar SDK para linux](https://developer.android.com/studio/index.html?hl=es-419)
* Descomprimir  
`tar xvzf ~/android-sdk*.tgz -C /tmp/`
* `sudo su`  
* `apt-get install lib32z1 lib32ncurses5 lib32stdc++6`
* `chown -R root:root /tmp/android-sdk-linux*`
* `chmod -R +xr /tmp/android-sdk-linux*`
* `mv /tmp/android-sdk-linux* /opt/android-sdk-linux`
* Agregar al path
* `exit`
* `vim ~/.bashrc`
* Agregar la siguiente linea al final del archivo  
`export PATH=/opt/android-sdk-linux/tools:$PATH`
* Refrescar path  
`bash`
* Abrir SDK  
`android` o `android sdk`
* Instalar paquetes del SDK para las versiones de Android necesarias

## Crear Android Virtual Devices (AVD)
* Abrir AVD
`android avd`
* Crear imágenes de dispositivos con las características deseadas

## Instalar Apache Cordova
* `sudo add-apt-repository ppa:cordova-ubuntu/ppa`
* `sudo apt-get update`
* `sudo apt-get install cordova-cli`