- Model
- Administration Site
- Form Processing

### Learning Objectives

- Understand the Model-Template-View (MTV) architecture of Django.
- Learn how to define and manage models in Django.
- Gain proficiency in using Django's admin interface for database management.
- Develop skills to create and process forms in Django applications.

## The MTV Development Pattern

---

### Understanding Model in Django

---

- the single, definitive source of information about your data.
- contains the essential fields and behaviors of the data you’re storing

- Each model - Python class that subclasses `django.db.models.Model`
- Each attribute - a database field
- Automatically-generated database-access API

##### Defining a Model in Python

##### First Model - Quick Example

```python
  from django.db import models

  class Song(models.Model):
      title = models.CharField(max_length=100) # field of the model and maps to a database column
      lyrics = models.TextField()
      released_date = models.DateField(null=True, blank=True)
      is_published = models.BooleanField(default=False)
```

##### First Model - Database Representation

- Dabase Table - _songs_song_

??? info "Table Structure"
| Column Name | Data Type | Description |
|----------------|--------------|---------------------------------|
| id | Integer | Auto-incrementing primary key |
| title | Varchar(100) | Title of the song |
| lyrics | Text | Lyrics of the song |
| released_date | Date | Release date of the song |
| is_published | Boolean | Publication status of the song |

- Table name - appname_modelname
- In this case, the app name is `songs` and the model name is `Song`, resulting in the table name `songs_song`.
- An `id` field is automatically added as the primary key if not explicitly defined.

### Adding Model String Representations

#### Installing the Model

Process of having Django create the necessary database tables based on the defined models.

##### Creating Migrations

- creating migration class files that describe the changes to be made to the database schema.

```bash
  python manage.py makemigrations
```

![alt text](assets/output-makemigrations.png)

##### Applying Migrations

- applying the migrations to the database, creating or modifying tables as specified in the migration files.
- needs to be run whenever there are new migrations to apply.
- requires database connectivity.

```bash
  python manage.py migrate
```

---

### Let's Get Started - Setting Up the Database

---

### [Setting up the MySQL Database server and Creating a Database](database-setup.md)

### Database Settings for Django

- Update the `DATABASES` setting in your Django project's `settings.py` file to configure the connection to your MySQL database.

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<database-name>',
        'USER': '<djangouser>',
        'PASSWORD': '<djangopassword>',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

### Running App Migrations

```bash
python manage.py migrate songs
```
