# Guía de inicio rápido: Compose y Django por Mario Medina

Esta guía de inicio rápido demuestra cómo usar Docker Compose para configurar y ejecutar una aplicación simple de Django REST framework y migraciones a MySQL. Antes de empezar,
[instala Compose](https://docs.docker.com/compose/install/).

### Software utilizado

```
Django==4.1.5
django-cors-headers==3.13.0
djangorestframework==3.14.0
djangorestframework-simplejwt==5.2.2
mysqlclient==2.1.1
Mysql==8
```


## Deploy con docker compose

```
$ docker compose up -d
```

## Resultados esperados

La lista de contenedores debe mostrar dos contenedores en ejecución y la asignación de puertos como se muestra a continuación:
```
$ docker ps
CONTAINER ID   IMAGE               COMMAND                  CREATED         STATUS                   PORTS                               NAMES
da99ae07fbe9   dockerproject-web   "python manage.py ru…"   4 minutes ago   Up 3 minutes             0.0.0.0:8085->8000/tcp              docker_python_web
c0c3edfe3957   mysql:8             "docker-entrypoint.s…"   4 minutes ago   Up 4 minutes (healthy)   33060/tcp, 0.0.0.0:3308->3306/tcp   docker_python_db

```

Después de que se inicie la aplicación, vaya a `http://localhost:8085` en su navegador web.

## Crear super usuario

Crea super usuario usando el comando createsuperuser:
```
$ docker exec -it docker_python_web python manage.py createsuperuser --username=mario --email=mario@correo.com 
```

Se solicitará una contraseña. Después de ingresar una, el usuario se creará inmediatamente.

Luego vaya a `http://localhost:8085/admin` en su navegador web e ingrese el usuario y contraseña creado.