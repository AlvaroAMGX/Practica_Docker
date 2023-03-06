# Ejercicio 3
## Despliegue de la aplicación Guestbook:
Primero vamos a crear una red llamada guestbook:
```bash
docker network create red_guestbook
```
Y ahora ejecutaremos los dos contenedores:
```bash
docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes

docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook
```
Si ahora un docker ps -a podremos ver que estan los dos contenedores encendidos:  
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker21.png)
Si ahora vamos a localhost que esta conectado con nuestro puerto 80 podremos ver directamente la aplicación guestbook:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker22.png)
## Despliegue de la aplicación Temperaturas:
Primero vamos a crear una red llamada temperaturas:
```bash
docker network create red_temperaturas
```
Y ahora ejecutaremos los dos contenedores:
```bash
docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend

docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
```
Si ahora un docker ps -a podremos ver que estan los dos contenedores encendidos:  
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker23.png)
Si ahora vamos a localhost que esta conectado con nuestro puerto 80 podremos ver directamente la aplicación temperaturas:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker24.png)
## Despliegue de Wordpress + mariadb
Primero vamos a crear una red llamada red_wp:
```bash
docker network create red_wp
```
Y ahora ejecutaremos los dos contenedores:
```bash
docker run -d --name servidor_mysql \
                --network red_wp \
                -v /opt/mysql_wp:/var/lib/mysql \
                -e MYSQL_DATABASE=bd_wp \
                -e MYSQL_USER=user_wp \
                -e MYSQL_PASSWORD=asdasd \
                -e MYSQL_ROOT_PASSWORD=asdasd \
                mariadb
                
docker run -d --name servidor_wp \
                --network red_wp \
                -v /opt/wordpress:/var/www/html/wp-content \
                -e WORDPRESS_DB_HOST=servidor_mysql \
                -e WORDPRESS_DB_USER=user_wp \
                -e WORDPRESS_DB_PASSWORD=asdasd \
                -e WORDPRESS_DB_NAME=bd_wp \
                -p 80:80 \
                wordpress
```
Si ahora un docker ps -a podremos ver que estan los dos contenedores encendidos:  
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker25.png)
Si ahora vamos a localhost que esta conectado con nuestro puerto 80 podremos ver directamente la aplicación de wordpress:  
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker26.png)
