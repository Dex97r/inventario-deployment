# Checklist de Capturas Requeridas para el Informe Final

Este documento sirve como guía y lista de verificación para recopilar las evidencias del despliegue y funcionamiento del sistema completo de inventario.

---

## 1. Evidencias de Infraestructura y Despliegue (Docker)

*   [ ] **Repositorios creados**
    *   *Descripción:* Captura de pantalla de la estructura del proyecto en el explorador de archivos o en el repositorio Git remoto (GitHub/GitLab) mostrando los tres proyectos: `inventario-api`, `inventario-webapp` e `inventario-deployment`.
*   [ ] **Estructura de carpetas**
    *   *Descripción:* Captura del árbol de directorios de `inventario-deployment` en el IDE (ej. VS Code) mostrando la carpeta `docs` y los archivos de configuración en la raíz.
*   [ ] **Docker Compose**
    *   *Descripción:* Captura del archivo `docker-compose.yml` abierto en el editor para evidenciar la configuración de los 4 servicios y redes.
*   [ ] **`docker compose ls`**
    *   *Descripción:* Ejecución del comando en la terminal para mostrar el proyecto activo en compose.
*   [ ] **`docker container ls`**
    *   *Descripción:* Ejecución en consola mostrando los 4 contenedores (`webapp`, `db_webapp`, `api_service` y `db_api`) con sus puertos y nombres correspondientes.
*   [ ] **Contenedores ejecutándose (Logs de Inicio)**
    *   *Descripción:* Captura de la terminal con el comando `docker compose logs -f` o la terminal de `docker compose up --build` después de que todos los servicios hayan pasado sus healthchecks satisfactoriamente.

---

## 2. Evidencias de Interfaz de Usuario (WebApp Flask - `http://localhost`)

*   [ ] **Login**
    *   *Descripción:* Captura de pantalla de la pantalla de inicio de sesión (`/login` o raíz `/`), mostrando los campos del formulario listos para ingresar las credenciales de demo (`admin@demo.com` / `admin123`).
*   [ ] **Registro**
    *   *Descripción:* Captura de pantalla del formulario de registro de nuevos usuarios en la WebApp (`/register` o `/registro`), mostrando los campos de validación del formulario.
*   [ ] **Dashboard**
    *   *Descripción:* Vista principal una vez autenticado, donde se muestren estadísticas globales de los equipos tecnológicos del inventario (ej. cantidad de laptops, impresoras, estados de equipos).
*   [ ] **Lista de equipos**
    *   *Descripción:* Captura de la tabla que lista los equipos del inventario consumidos dinámicamente desde la API.
*   [ ] **Crear equipo**
    *   *Descripción:* Captura de pantalla del formulario de ingreso de un nuevo activo (equipo) tecnológico con datos ficticios.
*   [ ] **Editar equipo**
    *   *Descripción:* Formulario de edición mostrando la carga de datos del equipo seleccionado previamente.
*   [ ] **Eliminar equipo**
    *   *Descripción:* Captura de pantalla del cuadro de diálogo/modal de confirmación de borrado o mensaje emergente indicando la eliminación correcta del activo.

---

## 3. Evidencias de API y Documentación (FastAPI - `http://localhost:8000`)

*   [ ] **Swagger UI**
    *   *Descripción:* Captura de pantalla de la página interactiva `http://localhost:8000/docs` donde se visualicen todos los endpoints CRUD (`GET`, `POST`, `PUT`, `DELETE` en `/equipos` y `/equipos/estadisticas/resumen`) y se demuestre que responde correctamente tras hacer clic en "Try it out".
