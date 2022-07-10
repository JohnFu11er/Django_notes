### start a django project
```
django-admin startproject <project_name>
```

### Verify operation of development server
- Change directory into the <project_name> directory
- Run the development server
  ```
  python3 manage.py runserver
  ```

### Variations on running the development server
- Open the `<project_name>/<project_name>/settings` file and add an IP address of a computer that is allowed to access the server.
- Add to the list of `ALLOWED_HOSTS`:
  - IP addresses (The hosting server's address)
  - URL's (The hosting server's URL)

- Run the server and allow access from any address on a specified port:
  - Example:
    ```
    python3 manage.py runserver 0:8080
    ```


### Install Postgresql
- Install postgresql
- Start the postgresql server
- Create a postgresql database


### Configuring the Django `settings.py` file
- Go to the django project's `settings.py` file
- Edit the `DATABASES` entries (for example):
  ```python
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.postgresql',
          'NAME': 'test',
          'HOST': '127.0.0.1',
          'PORT': '5432',
      }
  }
  ```
- Add your application to the `INSTALLED_APPS` section:
  ```python
  INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
      'polls.apps.PollsConfig',  # <------ Line added for my app named polls
  ]
  ```
  > In this example the `PollsConfig` function is in the `apps.py` program in the `polls` directory


### Edit the `models.py` file
- Create a `class` for your new model and inherit models.Model:
  ```python
  class Listings(models.Model):
      class Meta:
          verbose_name = "Listings"
          verbose_name_plural = "Listings"
  
      name = models.CharField(max_length=50)
      category = models.CharField(choices=CATEGORY, max_length=6)
  
      def __str__(self):
          return self.name
  ```
  > Class variables will indicate fields in the database model (`name` and `category` in this case)

- Example:
  ```python
  from django.db import models
  
  CATEGORY = (
      ('DRAMA', 'Drama'),
      ('ACTION', 'Action')
  )
  
  class Listings(models.Model):
      class Meta:
          verbose_name = "Listings"
          verbose_name_plural = "Listings"
  
      name = models.CharField(max_length=50)
      category = models.CharField(choices=CATEGORY, max_length=6)
  
      def __str__(self):
          return self.name
  ```


### Register your model in the `admin.py` file
- Import admin from django.contrib:
  ```python
    from django.contrib import admin
  ```

- Import your model class ("Listings" in this example) from the `models.py` file in the same directory that you created above:
  ```python
  from .models import Listings
  ```

- Register your model class ("Listings" in this example) with the admin site:
  ```python
  admin.site.register(Listings)
  ```

- Example:
  ```python
  from django.contrib import admin
  
  from .models import Listings
  
  admin.site.register(Listings)
  ```