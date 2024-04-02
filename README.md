# L1Proyecto
# Crear un entorno virtual
python -m venv hello

# Activar el entorno virtual (en Windows)
cd hello
Scripts\activate

# Instalar Django
pip install django

# Verificar las dependencias instaladas
pip freeze

# Crear un nuevo proyecto Django
django-admin startproject helloworld

# Cambiar al directorio del proyecto
cd helloworld

# Crear una nueva aplicación dentro del proyecto
python manage.py startapp myhelloapp

# Agregar la aplicación al archivo settings.py
# settings.py
INSTALLED_APPS = [
    ...
    'myhelloapp',
]

# Crear las migraciones para la nueva aplicación
python manage.py makemigrations myhelloapp

# Aplicar las migraciones
python manage.py migrate

# Crear un archivo HTML básico en la carpeta de plantillas de la aplicación
# Crear un directorio "templates" en la carpeta de la aplicación "myhelloapp"
mkdir myhelloapp/templates
# Crear un archivo "index.html" dentro del directorio "templates"
<!DOCTYPE html>
<html lang='es'>
<head>
    <meta charset='UTF-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1.0'>
    <title>Página de inicio</title>
</head>
<body>
    <h1>Hola mundo, hola Django</h1>
</body>
</html>

# Modificar views.py dentro de la aplicación para renderizar el archivo HTML
# views.py
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')

# Crear urls.py dentro de la aplicación para definir las rutas
# urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]

# Modificar urls.py en el directorio del proyecto para incluir las rutas de la aplicación
# urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myhelloapp.urls'))
]

# Ejecutar el servidor de desarrollo
python manage.py runserver

# Cerrar entorno virtual
deactivate

# Crear archivo requiremenst.txt
pip freeze > requirements.txt

