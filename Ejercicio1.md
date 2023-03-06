# Ejercicio 1
## A realizar :
### Basico
- Ejecuta la imagen "hello-world" 

Para ejecutar la imagen hello-world lo que haremos sera usar el comando:
```bash
docker run hello-world
```
Tardara un poco de tiempo ya que al ser la primera vez que ejecuto un contenedor basado en esa imagen,despues nos dara un mensaje en el que nos dira hola y nos dara mas ejemplos y explicaciones de lo que acaba de hacer:  
![Docker prueba hello world](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker1.png)
- Muestra las imágenes Docker instaladas  

Para ver que imagenes tenemos instaladas usaremos el comando
```bash
docker image ls
```
Esto nos hara un listado con el repositorio,la versión descargada,la id de la imagen,cuando se creo y el tamaño que ocupa:  
![Docker prueba image ls](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker2.png)


- Muestra los contenedores Docker

Para ver que nuestros contenedores docker usaremos el comando:
```bash
docker container ls -a
```
Nos mostrara un listado con nuestros contenedores el cual nos dira su id,la imagen utilizada,si tiene algun comando que podamos usar,cuando fue creada,su status,si tiene algun puerto abierto y su nombre:
![Docker container ls -a](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker3.png)
### Primer Dockerfile  
- Edita el fichero Dockerfile  
Primero vamos a  conseguir una aplicación para probar:
```bash
git clone https://github.com/docker/getting-started.git
```
Para empezar a editarlo comenzaremos  este comando **sudo nano Dockerfile** tendremos que hacerlo dentro de esta ruta getting-started/app:
```bash
touch Dockerfile
---------------
# Dentro pondremos esto

# syntax=docker/dockerfile:1
   
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
- Construye el contenedor
Para construirlo usaremos el comando docker build,haremos esto:
```bash
docker build -t getting-started .
```
Empezara a construirlo y en poco tiempo lo dejara listo
- Ejecútalo
Para ejecutarlo usaremos este comando:
```bash
docker run -dp 3000:3000 getting-started
```
Si nos vamos a http://localhost:3000 nos deberia salir esto:  
![funciona](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker6.png)
- Create una cuenta en hub.docker.com  
Aqui hay una captura de que tengo cuenta creada:  
![cuenta](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker5.png)  
- Publícalo  
Para publicarlo habra que cumplir varios requisitos:  
  - Primero deberemos tener una cuenta y conectarla con docker login y meter nuestras credenciales
  - Segundo le cambiamos el tag con este comando:
```bash
sudo docker tag getting-started:latest elgordoasesino/prueba:prueba
```
  - por ultimo usaremos este comando:
```bash
sudo docker push elgordoasesino/prueba:prueba
```
Y ya habremos subido la imagen para comprobarlo podremos ir a docker hub y veremos que esta subida:  
![cuenta](https://github.com/AlvaroAMGX/Practica_Docker/blob/main/Imagenes/docker7.png)  
