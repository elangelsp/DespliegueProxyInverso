# Despliegue Completo Angel Cabrera Martos

Este proyecto implementa una aplicación web completa con frontend en React, backend en Symfony, una base de datos MySQL y un servicio de phpmyadmin para gestionar la base de datos, todo ello desplegado con Docker.

## Requisitos Previos

- Docker y Docker Compose instalados
- Git

## Configuración Inicial

### 1. Clonar el Repositorio

```bash
    git clone https://github.com/elangelsp/Despliegue.git
```

### 2. Configuración del Archivo .env

Crea un archivo `.env` en la raíz del proyecto con el siguiente contenido:
```bash
# Credenciales MySQL
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=database
MYSQL_USER=user
MYSQL_PASSWORD=password

# Configuración Backend
DATABASE_URL="mysql://user:password@database:3306/myapp"
```

### 3. Certificados SSL

Los certificados SSL se generarán automáticamente en la primera ejecución en el directorio `web/certs/`. No es necesario realizar ninguna acción manual.

### 4. Iniciar la Aplicación
```bash
docker-compose up -d
```

## Acceso a los Servicios

Una vez iniciada la aplicación, podrás acceder a:

- Frontend: https://localhost
- PHPMyAdmin: http://localhost:8080
  - Usuario: user
  - Contraseña: password
- API Backend: https://localhost/api/db

## Estructura del Proyecto

- `/frontend`: Aplicación React
- `/backend`: API Symfony
- `/web`: Configuración de Nginx y SSL
- `/database`: Scripts de inicialización de la base de datos

## Seguridad

- Los certificados SSL y el archivo .env están configurados para no subirse al repositorio
- Las credenciales de la base de datos solo son accesibles dentro de la red de Docker
- El proxy inverso (Nginx) gestiona todas las conexiones HTTPS

## Mantenimiento

Para detener la aplicación:
```bash
docker-compose down
```

Para reconstruir los contenedores:
```bash
docker-compose up -d --build
```
