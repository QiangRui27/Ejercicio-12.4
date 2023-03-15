# Seleccionamos nuestra imagen base ()
FROM nginx:1.23
 
# Instalamos el software necesario
RUN apt update\
    && apt install git -y

# Clonamos el repositorio con el codigo fuente
RUN git clone https://github.com/josejuansanchez/2048.git /tmp \
    && cp -R /tmp/2048/* /usr/share/nginx/html 

# Indicamos el puerto donde estará el servicio nginx (si no se indica al lanzar el comando)
EXPOSE 80

ENTRYPOINT [ "nginx" "-B", "'daemon off;'" ]
