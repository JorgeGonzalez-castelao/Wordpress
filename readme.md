

Por supuesto, aquí tienes una versión estilizada y con un formato más apropiado para un README de GitHub:

```markdown
# Configuración de Docker Compose para WordPress

Este repositorio contiene un archivo `docker-compose.yml` que permite configurar un entorno de WordPress con una base de datos MariaDB utilizando Docker Compose. A continuación, se describen los principales elementos de la configuración.

## Servicio "db" (Base de Datos)

```yaml
db:
  image: mariadb:10.6.4-focal
  command: '--default-authentication-plugin=mysql_native_password'
  volumes:
    - db_data:/var/lib/mysql
  restart: always
  environment:
    - MYSQL_ROOT_PASSWORD=somewordpress
    - MYSQL_DATABASE=wordpress
    - MYSQL_USER=wordpress
    - MYSQL_PASSWORD=wordpress
  expose:
    - 3306
    - 33060
```

1. **Imagen**: Utiliza la imagen MariaDB 10.6.4-focal.
2. **Autenticación**: Configura el contenedor para usar el método de autenticación `mysql_native_password`.
3. **Persistencia**: Mapea el volumen `db_data` para almacenar datos de la base de datos de forma persistente.
4. **Reinicio automático**: Configura el reinicio automático del contenedor en caso de fallo o después de un reinicio del sistema.
5. **Variables de entorno**: Define variables de entorno para la contraseña de root y los datos de la base de datos.
6. **Puertos expuestos**: Expone los puertos 3306 y 33060 para permitir la comunicación con otros contenedores.

## Servicio "wordpress"

```yaml
wordpress:
  image: wordpress:latest
  volumes:
    - wp_data:/var/www/html
  ports:
    - 80:80
  restart: always
  environment:
    - WORDPRESS_DB_HOST=db
    - WORDPRESS_DB_USER=wordpress
    - WORDPRESS_DB_PASSWORD=wordpress
    - WORDPRESS_DB_NAME=wordpress
```

1. **Imagen**: Utiliza la última imagen disponible de WordPress.
2. **Persistencia**: Mapea el volumen `wp_data` para almacenar archivos y datos de WordPress de forma persistente.
3. **Puertos mapeados**: Mapea el puerto 80 del host al puerto 80 del contenedor WordPress para permitir el acceso a través del puerto 80.
4. **Reinicio automático**: Configura el reinicio automático del contenedor en caso de fallo o después de un reinicio del sistema.
5. **Variables de entorno**: Configura las variables de entorno necesarias para que WordPress se conecte a la base de datos.

## Pasos para instalar WordPress con Docker Compose

1. Clona este repositorio en tu máquina local:

   ```bash
   git clone <URL_DEL_REPOSITORIO>
   ```

2. Asegúrate de tener Docker y Docker Compose instalados en tu sistema. Si no los tienes instalados, sigue las instrucciones en el sitio web oficial de Docker: [Instalación de Docker](https://docs.docker.com/get-docker/) y [Instalación de Docker Compose](https://docs.docker.com/compose/install/).

3. Abre una terminal y navega al directorio del repositorio clonado:

   ```bash
   cd <NOMBRE_DEL_DIRECTORIO>
   ```

4. Ejecuta el siguiente comando para iniciar WordPress:

   ```bash
   docker-compose up -d
   ```

   Esto levantará los contenedores de WordPress y MariaDB en segundo plano.

5. Abre un navegador web y accede a `http://localhost:80`. Deberías ver la página de configuración inicial de WordPress.

6. Sigue las instrucciones en pantalla para configurar WordPress y crear tu sitio.

## Captura de WordPress funcionando




Adjunta


