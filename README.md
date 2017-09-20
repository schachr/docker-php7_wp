# docker-php7_wp
Docker PHP7 Container for Wordpress

## Included PHP Extensions

    gd 
    mysqli 
    opcache 
    tidy

## OPcache settings
Recommended PHP.ini settings. See https://secure.php.net/manual/en/opcache.installation.php

    opcache.memory_consumption=128
    opcache.interned_strings_buffer=8
    opcache.max_accelerated_files=4000
    opcache.revalidate_freq=60
    opcache.fast_shutdown=1
    opcache.enable_cli=1


## Usage
You need to pass the needed directories inside the container. You can map `www.conf` inside as well to change the properties to your needs. `pm.status_path` is already set to `/status`.

Example:

    docker run \
    -d \
    --restart=always \
    --name php7-wp \
    -h "docker-php7-wp" \
    -v ${PWD}/www.conf:/usr/local/etc/php-fpm.d/www.conf \
    -v /var/www/wordpress:/var/www/wordpress \
    -p 127.0.0.1:9101:9000 schachr/php7_wp
