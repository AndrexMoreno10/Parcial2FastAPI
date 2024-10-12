# FastAPI User Management with Docker

## Descripción

Este proyecto es una API de gestión de usuarios construida con FastAPI y MySQL, ejecutada en contenedores Docker. Incluye migraciones de base de datos con Peewee, configuración mediante archivos .env, y análisis de calidad de código con Pylint. El proyecto está diseñado para un fácil despliegue y gestión a través de Docker, lo que facilita la instalación y configuración del entorno.


## Requisitos previos

Asegúrate de tener instaladas las siguientes herramientas en tu máquina:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Python 3.12](https://www.python.org/)

## Clonar el repositorio

Primero, clona este repositorio en tu máquina local:

```bash
   git clone https://github.com/AndrexMoreno10/Parcial2FastAPI
   cd Parcial2FastAPI
```


## Estructura del proyecto

- app/
  - helpers/: Funciones de ayuda y utilidades.
  - migrations/: # Migraciones de la base de datos utilizando Peewee.
  - models/: Definición de los modelos de la base de datos.
  - routes/: Rutas de la API para la gestión de usuarios.
  - services/: Lógica de negocio.
  - main.py: Archivo principal para ejecutar la API.
  - database.py: Configuración de la conexión a la base de datos MySQL.
  
- Dockerfile: Archivo para construir la imagen Docker de la aplicación.
- docker-compose.yml: Archivo para la orquestación de servicios Docker, incluyendo la aplicación FastAPI y la base de datos MySQL.
- .env: Variables de entorno utilizadas por Docker y la base de datos.
- .pylintrc: Archivo de configuración para el análisis de código con Pylint.
- requirements.txt: Dependencias del proyecto.
- MySQL/: Carpeta que contiene datos relacionados con la base de datos MySQL.


### Configuración

1. Crea un archivo .env en la raíz del proyecto y define las siguientes variables:
    DB_HOST=mysql
    DB_USER=root
    DB_PASSWORD=rootpassword
    DB_NAME=gestionusuarios


2. Crea y activa un entorno virtual (opcional pero recomendado):
```bash
python3 -m venv venv
source venv/bin/activate  # En Linux/macOS
.\venv\Scripts\activate  # En Windows
```
3. Instala las dependencias del proyecto:
```bash
pip install -r requirements.txt
```
4. Configura las variables de entorno necesarias.
5. Inicia la aplicación.


## Instrucciones de Ejecución con Docker

1. Construimos los contenedores Docker: 

Este comando construirá la imagen de la aplicación FastAPI y MySQL, y los levantará como contenedores:
```bash
    docker-compose up --build
```
2. Aplica las migraciones a la base de datos:
```bash
    docker-compose exec fastapi python -m app.migrations
```
4. Accede a la aplicación en tu navegador:
```bash
http://localhost:8000
```
5. La documentación de la API estará disponible en:
```bash
http://localhost:8000/docs.
```

### Análisis de calidad de código

Ejecutar migraciones de la base de datos
El proyecto utiliza peewee_migrate para gestionar las migraciones. Puedes aplicar las migraciones ejecutando el siguiente comando dentro del contenedor FastAPI:
```bash
    docker-compose exec fastapi python -m app.migrations
```
    
## Análisis de calidad de código

###  Configuracion PYLINT 
El proyecto utiliza Pylint para verificar la calidad del código. A continuación se muestran los pasos para ejecutarlo:


1. Instalación de Pylint (Si no tienes Pylint instalado en tu entorno virtual o local, puedes instalarlo con el siguiente comando)
```bash
pip install pylint
```

2. Verifica que la instalación fue exitosa ejecutando:
```bash
pylint --version
```

3. Para analizar todo el proyecto, asegúrate de estar en el directorio raíz del proyecto y ejecuta el siguiente comando:
```bash
pylint app/
```
4. Si deseas analizar un archivo específico, ejecuta el siguiente comando, reemplazando <archivo> por la ruta del archivo que deseas verificar:
```bash
pylint app/<archivo>.py
```

## Configuracion De PEP8:
PEP8 es la guía de estilo para escribir código Python limpio y legible. Aquí hay algunos puntos clave a seguir:

 - Usa 4 espacios por nivel de indentación.
 - Limita las líneas a un máximo de 79 caracteres.
 - Utiliza una línea en blanco para separar funciones y clases.
 - Los nombres de las variables y funciones deben ser en minúsculas con palabras separadas por guiones bajos (snake_case).
 - Usa nombres de clases en formato CamelCase.
   
Para aplicar las normas de PEP8 automáticamente, puedes usar Black como formateador de código.

## Configuracion De Black:
Black es una herramienta que formatea el código Python automáticamente siguiendo las reglas de PEP8.

1. Si no tienes Black instalado, puedes agregarlo ejecutando:
```bash
pip install black
```
2. Para formatear todo tu proyecto, asegúrate de estar en el directorio raíz del proyecto y ejecuta el siguiente comando:
```bash
black app/
```
3. Si deseas formatear un archivo específico, puedes hacerlo con el siguiente comando:
```bash
black app/<archivo>.py
```
4. Si deseas ver los cambios antes de aplicarlos, ejecuta Black en modo de comprobación:
```bash
black --check app/
```
