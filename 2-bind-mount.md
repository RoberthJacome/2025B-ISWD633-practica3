# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
docker run -d --name web-nginx -p 8080:80 -v C:/Users/miusuario/nginx/html:/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
Aparece el error Forbidden 403, pero abajo se eso se nombra al servidor web nginx/1.29.2

### ¿Qué pasa con el archivo index.html del contenedor?
No existe, por eso aparece el error.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Ahora si ya aparece el template que descargué.

### Eliminar el contenedor
docker rm -f web-nginx

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
Se crea sin problema, y  además los datos que alojé en el contenedor anterior siguen funcinando para el nuevo contenedor.
Por lo que mientras vuelva a utilizar la imagen en el mismo directorio, nginx se desplegará sin problemas. Sin embargo, 
se debe evitar utilizar los mismos puertos si se quiere crear más contenedores que funcionen.


