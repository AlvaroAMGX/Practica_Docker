# Ejercicio 5
## Construcción de imágenes con una página estática
Deberemos tener un fichero llamado Dockerfile y un directorio que se llamara public_html con un index.html dentro tiene una etiqueta h1 que pone **esto funciona**,dentro del dockerfile meteremos esto:
```bash
FROM debian
RUN apt-get update && apt-get install -y apache2 && apt-get clean && rm -rf /var/lib/apt/lists/*
ADD public_html /var/www/html/
EXPOSE 80
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```
Ahora para crear la imagen usamos este comando:
```bash
docker build -t josedom24/ejemplo1:v1 .
```
Si usamos docker images podremos ver la imagen que acabamos de crear:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker30.png) 
Por ultimo vamos a crear un contenedor con esta imagen
```bash
docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v1
```
Aqui podremos ver como ha funcionado:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker31.png) 
## Construcción de imágenes con una una aplicación PHP
Deberemos tener un fichero llamado Dockerfile y un directorio que se llamara app con un index.php dentro,dentro del dockerfile meteremos esto:
```bash
FROM debian
RUN apt-get update && apt-get install -y apache2 libapache2-mod-php7.4 php7.4 && apt-get clean && rm -rf /var/lib/apt/lists/*
ADD app /var/www/html/
RUN rm /var/www/html/index.html
EXPOSE 80
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```
Ahora para crear la imagen usamos este comando:
```bash
docker build -t josedom24/ejemplo2:v1 .
```
Si usamos docker images podremos ver la imagen que acabamos de crear:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker32.png) 
Por ultimo vamos a crear un contenedor con esta imagen
```bash
docker run -d -p 80:80 --name ejemplo2 josedom24/ejemplo2:v1
```
Aqui podremos ver como ha funcionado:
![foto docker](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker33.png) 
