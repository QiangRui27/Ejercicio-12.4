# Ejercicio-12.4

## 1 «Dockerizar» una web estática y publicarla en Docker Hub
En esta práctica tendremos que crear un archivo Dockerfile para crear una imagen Docker que contenga una aplicación web estática. Posteriormente deberá publicar la imagen en Docker Hub y realizar la implantación del sitio web en Amazon Web Services (AWS) haciendo uso de contenedores Docker y de la herramienta Docker Compose.

### 1.1 Tareas a realizar
A continuación se describen muy brevemente algunas de las tareas que tendrá que realizar.

1. Crea un archivo Dockerfile para crear una imagen que contenga el servicio de Nginx con la siguiente aplicación web estática:

    - https://github.com/josejuansanchez/2048

2. Publica la imagen en Docker Hub.

3. Crea una máquina virtual Amazon EC2.

4. Instala y configura Docker y Docker compose en la máquina virtual.

5. Crea un archivo docker-compose.yml para poder desplegar la aplicación web estática en la máquina virtual de AWS.

6. Busque cuál es la dirección IP pública de su instancia y compruebe que puede acceder a la aplicación web desde una navegador web.

### 1.2 Requisitos del archivo Dockerfile
Tendrá que crear un archivo Dockerfile con los siguientes requisit###os:

- Como imagen base deberá utilizar la última versión de nginx.

- Instala el software necesario para poder clonar el repositorio de GitHub donde se encuentra la aplicación web estática.

- Clona el repositorio de GitHub donde se encuentra la aplicación web estática en el directorio /usr/share/nginx/html/, que es el directorio que utiliza Nginx, por defecto, para servir el contenido.

- El puerto que usará la imagen para ejecutar el servicio de Nginx será el puerto 80.

- El comando que se ejecutará al iniciar el contenedor será el comando nginx -g 'daemon off;'.

### 1.3 Creación de la imagen Docker a partir del archivo Dockerfile
Para crear la imagen de Docker a partir del archivo Dockerfile deberá ejecutar el siguiente comando.

~~~
docker build -t nginx-2048 .
~~~

Para comprobar que la imagen se ha creado correctamente podemos ejecutar el comando:

~~~
docker images
~~~

Para publicar la imagen en Docker Hub es necesario que en el nombre de la imagen aparezca nuestro nombre de usuario de Docker Hub. Por ejemplo, si mi nombre de usuario es josejuansanchez la imagen debería llamarse josejuansanchez/nginx-2048.

También es una buena práctica asignarle una etiqueta a la imagen. Por ejemplo, en este caso vamos a asignarle las etiquetas 1.0 y latest.

~~~
docker tag nginx-2048 josejuansanchez/nginx-2048:1.0
~~~
~~~
docker tag nginx-2048 josejuansanchez/nginx-2048:latest
~~~

Comprobamos que la imagen tiene el nombre y las etiequetas correctas:
~~~
docker images
~~~
### 1.4 Publicar la imagen en Docker Hub
Una vez que le hemos asignado un nombre correcto a la imagen y le hemos añadido las etiquetas, podemos publicarla en Docker Hub.

En primer lugar, tendremos que iniciar la sesión en Docker Hub con el comando:
~~~
docker login
~~~

Una vez iniciada la sesión, podemos publicar la imagen con el comando docker push. Tenemos que publicar la imagen con las dos etiquetas que hemos creado.

~~~
docker push josejuansanchez/nginx-2048:1.0
~~~
~~~
docker push josejuansanchez/nginx-2048:latest
~~~
