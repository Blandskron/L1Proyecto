#Django

---

## **Proyecto L1: Configuración Inicial de Django**

### **1. Crear un Entorno Virtual**

```bash
python -m venv hello
```

### **2. Activar el Entorno Virtual (Windows)**

```bash
cd hello
Scripts\activate
```

### **3. Instalar Django**

```bash
pip install django
```

### **4. Verificar Dependencias Instaladas**

```bash
pip freeze
```

### **5. Crear un Nuevo Proyecto Django**

```bash
django-admin startproject helloworld
```

### **6. Crear una Nueva Aplicación**

```bash
cd helloworld
python manage.py startapp myhelloapp
```

### **7. Configurar la Aplicación en `settings.py`**

```python
# settings.py
INSTALLED_APPS = [
    ...
    'myhelloapp',
]
```

### **8. Generar y Aplicar Migraciones**

```bash
python manage.py makemigrations myhelloapp
python manage.py migrate
```

### **9. Crear Archivo HTML Básico**

```bash
mkdir myhelloapp/templates
```

Dentro de `myhelloapp/templates`, crear `index.html`:

```html
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
```

### **10. Configurar las Vistas**

En `myhelloapp/views.py`:

```python
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```

### **11. Definir las Rutas**

En `myhelloapp/urls.py`:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

### **12. Incluir las Rutas de la Aplicación en el Proyecto**

En `helloworld/urls.py`:

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myhelloapp.urls'))
]
```

### **13. Ejecutar el Servidor de Desarrollo**

```bash
python manage.py runserver
```

### **14. Desactivar el Entorno Virtual**

```bash
deactivate
```

### **15. Crear Archivo `requirements.txt`**

```bash
pip freeze > requirements.txt
```

---

Este tutorial te guiará a través de la configuración inicial de un proyecto Django, desde la creación del entorno virtual hasta la ejecución del servidor de desarrollo. ¡Disfruta construyendo con Django! 🚀
