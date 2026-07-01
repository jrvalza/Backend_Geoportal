# Backend Geoportal

Backend desarrollado en Django para gestionar información geoespacial y datos relacionados con parques, calles, personas y usuarios.

## Descripción

Este proyecto expone una API en Django y está preparado para ejecutarse con Docker. El backend organiza la lógica en una aplicación principal llamada `appjuavaal2`, donde se definen modelos, vistas, rutas y módulos auxiliares para el procesamiento de datos.

## Tecnologías

- Python 3
- Django 5
- PostgreSQL + psycopg2
- Docker / Docker Compose
- Gunicorn

## Estructura del proyecto

```text
.
├── docker-compose.yml
├── docker-compose.prod.yml
├── create_tables.sh
├── init_db.sh
├── insert_values.sh
├── .env
├── .env.dev
└── juavaal2/
    ├── manage.py
    ├── requirements.txt
    ├── settings.py
    ├── appjuavaal2/
    │   ├── models.py
    │   ├── views.py
    │   ├── viewsUsers.py
    │   ├── urls.py
    │   ├── tests.py
    │   └── pycode/
    └── juavaal2/
        ├── settings.py
        ├── urls.py
        ├── wsgi.py
        └── asgi.py
```

## Requisitos previos

- Python 3.10 o superior
- Docker y Docker Compose
- PostgreSQL creado previamente y accesible

## Variables de entorno

Crea o ajusta los archivos `.env` y `.env.dev` con valores como los siguientes:

```env
POSTGRES_DB=tu_base
POSTGRES_USER=tu_usuario
POSTGRES_PASSWORD=tu_password
POSTGRES_HOST=tu_host
POSTGRES_PORT=5432
DEBUG=True
DJANGO_ALLOWED_HOSTS=localhost,127.0.0.1
DEVELOP_DOCKER_DJANGO_API_FORWARDED_PORT=8000
```

## Ejecutar con Docker

1. Asegúrate de que la base de datos exista y que la red `postgis_postgis` esté disponible.
2. Ejecuta:

```bash
docker compose up --build
```

La API quedará disponible en:

```text
http://localhost:8000
```

## Ejecutar localmente

```bash
cd juavaal2
python -m venv .venv
source .venv/bin/activate  # En Windows: .venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

## Crear superusuario

```bash
python manage.py createsuperuser
```

## Notas

- El proyecto está pensado para funcionar como backend de una aplicación geoportal.
- La lógica de negocio específica se encuentra en la carpeta `appjuavaal2/pycode`.
- Los scripts `create_tables.sh`, `init_db.sh` e `insert_values.sh` pueden utilizarse para preparar la base de datos y cargar datos iniciales.

## Licencia

Este proyecto no incluye una licencia definida en este momento.
