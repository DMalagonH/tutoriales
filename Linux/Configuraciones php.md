##Configuraciónes frecuentes de php.ini
    date.timezone = America/Bogota
    short_open_tag = Off
    memory_limit = 1024M
    post_max_size = 1000M
    upload_max_filesize = 1000M
    max_file_uploads = 1000

##Configuraciones para seguridad de sesiones
(http://php.net/manual/es/session.security.php)

    session.name = PHPSESSID (Cambiar PHPSESSID por otro nombre)
    session.cookie_lifetime = 0
    session.use_cookies = 1
    session.use_only_cookies = 1
    session.use_strict_mode = 1
    session.cookie_httponly = 1
    session.use_trans_sid = 0
    session.cache_limiter=nocache
    session.hash_function="sha256"
    
