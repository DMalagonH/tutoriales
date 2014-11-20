
## Minificación de archivos JavaScript y CSS con Grunt
http://7sabores.com/blog/introduccion-grunt
http://7sabores.com/blog/automatizar-la-minificacion-archivos-css-js-grunt

### Instalación
    * npm install grunt-cli -g
    * Crear package.json genérico en la aplicación
        {
            "name": "appname",
            "version": "0.0.0",
            "devDependencies": {
            }
        }
    * Instalar Grunt en el proyecto 
        npm install grunt --save-dev
    * Instalar plugin para concatenación de archvos
        npm install grunt-contrib-concat --save-dev
    * Instalar plugin para minificar js
        npm install grunt-contrib-uglify --save-dev
    * Instalar plugin para compilar stylus
        npm install grunt-contrib-stylus --save-dev
    * Instalar plugin para minificar css 
        npm install grunt-contrib-cssmin --save-dev
    * Instalar plugin para escuchar cambios de archivos
        npm install grunt-contrib-watch --save-dev

    
### Crear tareas en Grunt
    * Crear un archivo llamado Gruntfile.js
        'use strict';
     
        module.exports = function (grunt) {
         
            grunt.initConfig({
                pkg: grunt.file.readJSON('package.json'),
            });
         
            // Where we tell Grunt we plan to use some plug-ins.
            //grunt.loadNpmTasks('grunt-contrib-xxxx');
         
         
            // Where we tell Grunt what to do when we type "grunt" into the terminal.
            //grunt.registerTask('default', ['xxxx']);
        };
    * 

