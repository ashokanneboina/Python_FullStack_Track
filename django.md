

# **Django – Core Concepts**

## **1. Django Architecture (MVT)**

Django follows the Model-View-Template (MVT) architecture to separate different parts of an application:

* **Model**
  Defines the structure of the database. It represents tables and handles data operations such as creating, updating, and deleting records.

* **View**
  Contains the application logic. It processes incoming requests, interacts with models if needed, and returns a response.

* **Template**
  Responsible for the presentation layer. It displays data using HTML and Django Template Language (DTL).

This separation improves code readability, reusability, and maintainability.

---

## **2. Project Structure**

A Django project is organized into multiple files and directories:

* `manage.py` – Command-line tool to manage the project
* `settings.py` – Contains configurations like database, installed apps, middleware
* `urls.py` – Maps URLs to views
* `models.py` – Defines database schema
* `views.py` – Handles request-response logic
* `templates/` – Stores HTML files
* `static/` – Stores CSS, JavaScript, images

Projects can contain multiple apps, each handling a specific functionality.

---

## **3. Setup Commands**

### Install Django

```bash
pip install django
```

### Create Project and Run Server

```bash
django-admin startproject myproject
cd myproject
python manage.py runserver
```

### Create App

```bash
python manage.py startapp myapp
```

After creating the app, it must be added to `INSTALLED_APPS` in `settings.py`.

---

## **4. URL Routing**

URL routing connects user requests to the appropriate view functions.

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

Each URL pattern defines a path and the corresponding view that should handle it.

---

## **5. Views**

Views process requests and return responses such as HTML pages or data.

```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello, Django!")
```

Views can also render templates using `render()` for dynamic content.

---

## **6. Models and Database**

Models define how data is structured in the database using Python classes.

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
```

Django automatically converts these models into database tables using migrations.

### Apply Changes:

```bash
python manage.py makemigrations
python manage.py migrate
```

Django uses an ORM, allowing database interaction without writing SQL queries.

---

## **7. Templates**

Templates are used to generate dynamic HTML pages.

```html
<h1>Welcome {{ name }}</h1>
```

Django Template Language (DTL) allows variables, loops, and conditions inside HTML.

Example:

```html
{% for student in students %}
    <p>{{ student.name }}</p>
{% endfor %}
```

---

## **8. Admin Panel**

Django provides a built-in admin interface to manage data easily.

```bash
python manage.py createsuperuser
```

After logging in to the admin panel, models can be added, updated, or deleted without writing extra code.
Models must be registered in `admin.py` to appear in the admin panel.

---

## **9. Request–Response Flow**

1. User sends a request through a URL
2. Django matches the URL in `urls.py`
3. The corresponding view is called
4. View interacts with models (if required)
5. Data is passed to a template
6. Final response is sent back to the user



