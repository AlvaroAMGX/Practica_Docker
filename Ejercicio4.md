# Ejercicio 3
## Despliegue de la aplicación guestbook
Vamos a crear un fichero llamado docker-compose.yml y dentro le pondremos esto:
```bash
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    ports:
      - 80:5000
  db:
    container_name: redis
    image: redis
    restart: always
```
Ahora usaremos el comando docker-compose up -d para encenderlo,para comprobar si ha funcionado nos iremos a localhost:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker27.png)
Para apagarlo en vez de up usaremos stop y para eliminarlo down.
## Despliegue de la aplicación temperaturas
Vamos a crear un fichero llamado docker-compose.yml y dentro le pondremos esto:
```bash
version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
      - 80:3000
    depends_on:
      - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
```
Ahora usaremos el comando docker-compose up -d para encenderlo,para comprobar si ha funcionado nos iremos a localhost:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker28.png)
Para apagarlo en vez de up usaremos stop y para eliminarlo down.
## Despliegue de WordPress + Mariadb
Vamos a crear un fichero llamado docker-compose.yml y dentro le pondremos esto:
```bash
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - wordpress_data:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - mariadb_data:/var/lib/mysql
volumes:
    wordpress_data:
    mariadb_data:
```
Ahora usaremos el comando docker-compose up -d para encenderlo,para comprobar si ha funcionado nos iremos a localhost:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker29.png)
Para apagarlo en vez de up usaremos stop y para eliminarlo down.
