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
- Configuraciones previas
Primero Tendremos que crear dos archivos uno llamado Dockerfile y otro llamado main.py ya que necesitaremos estos archivos para crear el contenedor.  

Para crear los archivos usaremos estos comandos:
```bash 
sudo nano Dockerfile
sudo nano main.py
```
Para guardar el archivo y que no se borre al no ponerle nada le daremos al comando **Control+O**
- Edita el fichero Dockerfile
- Construye el contenedor
- Ejecútalo
- Create una cuenta en hub.docker.com
- Publícalo
