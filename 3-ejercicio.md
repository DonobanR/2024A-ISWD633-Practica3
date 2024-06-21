## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor es /var/lib/mysql
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?

La carpeta db del host contiene los archivos y directorios utilizados por MySQL para almacenar la base de datos, incluyendo los datos de las tablas, los índices, los archivos de log, y asi.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

```
docker run -d --name mysql-container --network net-wp -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_password -v C:\path\to\host\ejercicio3\db:/var/lib/mysql mysql:8
```

```
docker run -d --name wordpress-container --network net-wp -e WORDPRESS_DB_HOST=mysql-container:3306 -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_password -e WORDPRESS_DB_NAME=wordpress_db -v C:\path\to\host\ejercicio3\www:/var/www/html wordpress
```


### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Con un monton de archivos, entre estos carpetas, archivos .php, un readme.html y un licence.txt

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d --name wordpress-container --network net-wp \
-e WORDPRESS_DB_HOST=mysql-container:3306 \
-e WORDPRESS_DB_USER=wp_user \
-e WORDPRESS_DB_PASSWORD=wp_password \
-e WORDPRESS_DB_NAME=wordpress_db \
-v /path/to/host/ejercicio3/www:/var/www/html \
wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar el contenedor y crearlo nuevamente, las personalizaciones y las entradas en WordPress se conservan. Esto sucede porque los datos de la base de datos y los archivos de WordPress se almacenan en volúmenes montados en el host, asegurando que la información persista a través de la eliminación y recreación de contenedores.



