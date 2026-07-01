# 🗺️ Backend Geoportal

**Backend Geoportal** es una API REST desarrollada con [Django](https://www.djangoproject.com/), pensada para dar soporte a una aplicación tipo geoportal. Expone endpoints para consultar y gestionar entidades geoespaciales, con autenticación de usuarios por sesión para proteger las operaciones de escritura. El proyecto está totalmente **dockerizado**, con configuraciones diferenciadas para entornos de desarrollo y producción.

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-5.0-092E20?logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)
![Gunicorn](https://img.shields.io/badge/Gunicorn-Production-499848?logo=gunicorn&logoColor=white)

---

## 📑 Tabla de contenidos

- [Funcionalidades](#-funcionalidades)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Compilación e instalación](#️-compilación-e-instalación)
- [Variables de entorno](#-variables-de-entorno)
- [Tecnologías usadas](#-tecnologías-usadas)
- [Notas](#-notas)

---

## 🚀 Funcionalidades

- 🌐 API REST lista para ser consumida por un frontend web o móvil (CORS habilitado)
- 📍 Gestión de entidades geoespaciales del geoportal (consulta, alta, modificación y baja)
- 🔐 Autenticación de usuarios por sesión, con endpoints protegidos para las operaciones de escritura
- 🐳 Despliegue mediante Docker / Docker Compose, con perfiles separados de desarrollo y producción
- ⚙️ Configuración basada en variables de entorno, sin credenciales embebidas en el código

---

## 📁 Estructura del proyecto

```
Backend_Geoportal/
│
├── docker-compose.yml          # Orquestación en modo desarrollo
├── docker-compose.prod.yml     # Orquestación en modo producción
├── scripts/ (*.sh)             # Scripts auxiliares de gestión de la base de datos
│
└── juavaal2/                   # Proyecto Django
    ├── manage.py
    ├── requirements.txt
    ├── Dockerfile
    │
    ├── juavaal2/                # Configuración del proyecto (settings, urls, wsgi/asgi)
    └── appjuavaal2/             # Aplicación principal de la API (vistas, rutas, modelos y lógica de negocio)
```

---

## ⚙️ Compilación e instalación

### Con Docker (recomendado)

```bash
git clone https://github.com/jrvalza/Backend_Geoportal.git
cd Backend_Geoportal
```

Desarrollo (con recarga en caliente):

```bash
docker compose up --build
```

Producción:

```bash
docker compose -f docker-compose.prod.yml up --build -d
```

La API quedará disponible en `http://localhost:8000/`.

---

## 🔧 Variables de entorno

El proyecto lee su configuración desde ficheros `.env` / `.env.dev` / `.env.prod` (no incluido en el repositorio), con datos para la conexión a base de datos, el modo `DEBUG` y los puertos expuestos por cada entorno.

---

## 🧠 Tecnologías usadas

| Tecnología | Uso |
|---|---|
| ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) | Lenguaje principal |
| ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) | Framework web, enrutado, autenticación y sesiones |
| ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) | Empaquetado y orquestación de servicios |
| ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) | Base de datos |
| ![Gunicorn](https://img.shields.io/badge/gunicorn-%298729.svg?style=for-the-badge&logo=gunicorn&logoColor=white) | Servidor WSGI en producción |


---

## 📌 Notas

- El backend está pensado para funcionar como servicio independiente, consumido por un frontend web o una aplicación móvil de geoportal.
- La configuración diferenciada entre `docker-compose.yml` y `docker-compose.prod.yml` permite mantener un flujo de desarrollo ágil sin afectar al despliegue en producción.
