# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)

```
docker run -d --name mi-nginx -v C:\nginx\html:/usr/share/nginx/html nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?

Aunque se ha montado en el contenedor en la ruta /usr/share/nginx/html en mi local de C:\nginx\html no se me muestra nada :((

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html del contenedor es reemplazado por el archivo index.html del directorio html de la máquina host.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor de nginx del html, se verá el contenido de la carpeta html de la máquina host, ya que se ha montado en el contenedor en la ruta /usr/share/nginx/html.

### Eliminar el contenedor

Primero paras el contenedor, para luego borrarlo

```
docker rm -f mi_nginx
```

```
docker rm -f mi_nginx
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
Al crear nuevamente el mismo contenedor con el volumen de tipo host, nginx mostrará nuevamente el contenido de la carpeta html 

### ¿Qué hace el comando pwd?
muestra la ruta completa del directorio de trabajo actual.


Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

