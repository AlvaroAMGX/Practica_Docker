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
- Configuraciones previas  y modo de probar que funciona
Primero Tendremos que crear dos archivos uno llamado Dockerfile y otro llamado main.py ya que necesitaremos estos archivos para crear el contenedor.  

Para crear los archivos usaremos estos comandos:
```bash 
# Este archvio lo dejaremos en blanco
sudo nano Dockerfile
```
Para guardar el archivo y que no se borre al no ponerle nada le daremos al comando **Control+O**  
Dentro de main.py vamos a poner un print para comprobar que funciona correctamente:
```bash
sudo nano main.py
-----------------
#!/usr/bin/env python3

print("Este contenedor esta funcionando correctamente")
```
- Edita el fichero Dockerfile
Para empezar a editarlo comenzaremos  este comando:
```bash 
sudo nano Dockerfile
```
Ahora dentro de este archivo primero pondremos la imagen,luego le vamos a indicar que copie nuestro archivo main.py dentro del container y luego que lo ejecute en el terminal:
```bash
# Aqui le indicamos que imagen y que versión queremos en nuestro caso python y la ultima versión que es la más actualizada.
FROM python:latest

# Copiamos el archivo main.py que creamos antes para ver si el contenedor funciona.
COPY main.py /

# Aqui le decimos que ejecute el archivo que acabamos de copiar.
CMD [ "python", "./main.py" ]
```
- Construye el contenedor
Para construirlo usaremos el comando:
```bash
docker build -t Prueba-Python
```
- Ejecútalo
Para ejecutarlo usaremos el comando:
```bash 
docker run python-test
```
Nos deberia salir esto,lo que significara que esta correctamente realizado:

- Create una cuenta en hub.docker.com
- Publícalo
