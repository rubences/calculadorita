# calculadorita

Para usar Django, necesitarás organizar tus archivos de una manera específica y crear una aplicación Django en un nuevo archivo Python. Aquí está un ejemplo de cómo podrías hacerlo:

Organiza tus archivos de la siguiente manera:
                index.html
        __init__.py
        settings.py
        urls.py
        wsgi.py
    manage.py
En tu archivo settings.py, asegúrate de que 'mydjangoapp' esté en INSTALLED_APPS y que STATIC_URL esté configurado:
INSTALLED_APPS = [
    # otras apps
    'mydjangoapp',
]

STATIC_URL = '/static/'
En tu archivo urls.py, agrega una ruta para tu página de inicio:
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
Crea un nuevo archivo views.py en la misma carpeta que urls.py y settings.py, y agrega una vista para tu página de inicio:
from django.shortcuts import render

def home(request):
    return render(request, 'mydjangoapp/index.html')
En tu archivo index.html, enlaza el archivo CSS y el archivo JavaScript utilizando las etiquetas {% load static %}, <link> y <script> respectivamente:
{% load static %}
<head>
    <!-- Otros elementos del head -->

    <!-- Enlace al archivo CSS -->
    <link rel="stylesheet" type="text/css" href="{% static 'mydjangoapp/css/style.css' %}">
</head>
<body>
    <!-- Tu contenido HTML -->


Para ejecutar tu aplicación Django, abre una terminal, navega a la carpeta mydjangoapp y ejecuta python manage.py runserver. Tu aplicación debería estar disponible en http://localhost:8000.