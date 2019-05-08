##Build Laravel web using Docker Compose

 \

###Install dependencies for Web


**First, download the Laravel installer using Composer**
```Shell
composer global require laravel/installer
```

<br/>

**Then, create laravel project into directory web/**
```Shell
laravel new web && cd web/
```

<br/>

**To install vendor for laravel and reduce image size**
```Shell
docker run --rm -it web/:app composer:1.8
```
note: “--rm” command: when container has been stop, container will be delete itself after process stop.

<br/>

###Create docker-compose file

**docker-compose.yml**
```YAML
version: '3.2'
services:

  php:
    image: php:fpm-alpine
    container_name: php_www
    volumes:
      - ./web/:/var/www/html
    ports:
      - '9000'

  nginx:
    image: nginx:alpine
    container_name: nginx_host
    volumes:
      - ./config/nginx/:/etc/nginx/conf.d/
      - ./web/:/var/www/html
    ports:
      - 80:80
```

<br/>

###Run docker-compose file
\
go to directory lab_01_compose/  
```Shell
cd lab_01_compose/
```

<br/>

run following command to run container from ***docker-compose.yml***  

```Shell
docker-compose up -d
```

<br/>

Finally go to [localhost:80](localhost:80)

\
**Yay Happy developing!**