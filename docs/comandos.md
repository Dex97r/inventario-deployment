# Referencia de Comandos Docker y Docker Compose

Este documento contiene un compendio de los comandos necesarios para desplegar, administrar y depurar la arquitectura multicontenedor del sistema de inventario.

---

## 1. Comandos de Docker Compose (Ciclo de Vida)

### Iniciar el Despliegue Completo
Construye las imágenes locales si no existen (o si han cambiado), crea las redes y volúmenes, e inicia todos los contenedores en primer plano:
```bash
docker compose up --build
```
*Si desea iniciarlo en segundo plano (modo interactivo apagado), añada el flag `-d`:*
```bash
docker compose up --build -d
```

### Detener el Despliegue
Detiene y elimina los contenedores y las redes creadas por el despliegue actual, sin borrar los volúmenes persistentes:
```bash
docker compose down
```

### Detener el Despliegue Eliminando Volúmenes
Detiene los contenedores y elimina tanto las redes como los volúmenes de datos persistentes (las bases de datos volverán a su estado vacío inicial):
```bash
docker compose down -v
```

### Visualizar el Estado de los Servicios
Muestra el estado de ejecución, puertos y healthchecks de los contenedores asociados a este archivo `docker-compose.yml`:
```bash
docker compose ps
```

### Monitorear Logs de los Contenedores
Visualiza la salida estándar y de error de todos los servicios del proyecto en tiempo real:
```bash
docker compose logs -f
```
*Para ver logs de un contenedor específico:*
```bash
docker compose logs -f webapp
docker compose logs -f api_service
```

### Listar los Proyectos Activos de Compose
Muestra todos los proyectos de Docker Compose que se encuentran en ejecución en el sistema:
```bash
docker compose ls
```

---

## 2. Comandos Generales de Docker (Contenedores, Volúmenes y Redes)

### Listar Contenedores del Sistema
Lista todos los contenedores activos en el demonio de Docker local:
```bash
docker container ls
```
*Para ver todos los contenedores (activos e inactivos):*
```bash
docker container ls -a
```

### Listar Imágenes Locales
Muestra todas las imágenes Docker descargadas o construidas localmente:
```bash
docker images
```

### Listar Volúmenes de Datos
Muestra todos los volúmenes de almacenamiento creados en Docker:
```bash
docker volume ls
```

### Listar Redes Disponibles
Muestra las redes creadas por Docker:
```bash
docker network ls
```

---

## 3. Comandos de Depuración y Acceso Directo

### Acceder a la Consola de un Contenedor
Permite abrir una terminal interactiva (sh/bash) dentro de uno de los contenedores en ejecución:
```bash
# Acceder a la WebApp (Flask)
docker compose exec webapp sh

# Acceder al servicio API (FastAPI)
docker compose exec api_service sh
```

### Inspeccionar la Base de Datos PostgreSQL Directamente
Permite conectarse mediante `psql` para realizar consultas y verificar las tablas en caliente:
```bash
# Acceder a la base de datos de usuarios (db_webapp)
docker compose exec db_webapp psql -U webapp_user -d webapp_db

# Acceder a la base de datos de equipos (db_api)
docker compose exec db_api psql -U api_user -d api_db
```
*(Dentro del psql, puede ejecutar `\dt` para ver las tablas o `SELECT * FROM usuarios;` / `SELECT * FROM equipos;` para auditar los registros).*
