# Ejercicio 5
## Construcción de imágenes con una página estática
Deberemos tener un fichero llamado Dockerfile y un directorio que se llamara public_html con un index dentro,dentro del dockerfile meteremos esto:
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
