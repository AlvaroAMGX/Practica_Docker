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
