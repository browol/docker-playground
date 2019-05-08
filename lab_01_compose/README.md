##Build Laravel web using Docker Compose

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

go to directory lab_01_compose/  

```Shell
cd lab_01_compose/
```

run following command to run container from ***docker-compose.yml***  

```Shell
docker-compose up -d
```

then go to `localhost:80`

**Yay Happy developing!**