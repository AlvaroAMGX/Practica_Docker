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

