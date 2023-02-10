# Hello
Welcome to the Hello project! This project is designed for learning Django, Django Rest Framework, and Django GraphQL. It offers a range of features to help you organize and manage your personal and professional communication.

With this project, you'll be able to send and receive emails, chat with your contacts, create notes, tasks, and events, and even share these items with your contacts. The project also includes a feed feature, which shows updates from your contacts, groups, and yourself. Additionally, there's a trash app, which keeps track of deleted contacts, notes, emails, tasks, and feeds, so you can recover them if needed. And finally, there's a contacts app, which keeps your contact information, groups, and blocked contacts organized and accessible.

Whether you're new to Django or looking to improve your skills, the Hello project provides a great starting point to explore the features and capabilities of Django, Django Rest Framework, and Django GraphQL.

# Create project

```bash
mkdir hello
```

### Create virtual environment

```bash
pip install virtualenv
```

```bash
virtualenv mail # env_name is the name of the virtual environment
```

### Activate virtual environment

```bash
source mail/bin/activate
```

### Install requirements.txt

```bash
pip install -r requirements.txt
```

### Install Django

```bash
pip install django
```

### create requirements.txt

```bash
pip freeze > requirements.txt
```

### Create Django project

```bash
django-admin startproject hello . # project_name is the name of the project and . is the current directory
```

### Create Django app

```bash
python manage.py startapp app_name # app_name is the name of the app
```


### Create superuser

```bash
python manage.py createsuperuser
```


### Run server

```bash
python manage.py runserver
```


### Migrate

```bash
python manage.py migrate
```


### Create migrations

```bash
python manage.py makemigrations
```


### Project structure for outlook clone

### Planing to Hello in Django project for learning

1. Contacts app
   1. create contacts
      1. email, phone, address, first_name, last_name, company, avatar
   2. update contacts
   3. delete contacts -> put it in trash folder and delete after 30 days
   4. should be able to add contacts to groups
   5. block contacts
2. Email app
   1. message composition
   2. send and receive emails
   3. group emails to folders
   4. searching and filtering emails
   5. delete emails -> put it in trash folder and delete after 30 days
   6. user should be able to cc and bcc
   7. user should be able to attach files
3. Calendar app
   1. schedule events, appointments, meetings, tasks
   2. share calendar with other users in contacts
   3.  invite contacts to events and meetings
4. Notes app
   1. create notes
   2. update notes
   3. delete notes -> put it in trash folder and delete after 30 days
5. Tasks app
   1. create tasks and assign to contacts or groups or self
   2. update tasks
   3. delete tasks -> put it in trash folder and delete after 30 days
6. Chat app
   1. chat with contacts
   2. send notifications
   3. send files
   4. create groups
   5. invite contacts to groups
7. Feeds app
   1. show feeds from contacts
   2. show feeds from groups
   3. show feeds from self
   4. delete feeds
   5. others can comment, like, react on feeds
8. Trash app
   1. restore deleted contacts, notes, emails, tasks
   2. permanently delete contacts, notes, emails, tasks
   3. Feeds can be deleted permanently

### Create apps folder

```bash
python manage.py startapp contacts
python manage.py startapp emails
python manage.py startapp calendars
python manage.py startapp notes
python manage.py startapp tasks
python manage.py startapp chats
python manage.py startapp feeds
python manage.py startapp trash
```

### add THIRD_PARTY_APPS, and LOCAL_APPS apps to INSTALLED_APPS to settings.py

```python
# path ./hello/settings.py
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",

    # Third party apps

    # Local apps
    'contacts',
    'emails',
    'calendars',
    'notes',
    'tasks',
    'chats',
    'feeds',
    'trash',
]
```

### Install django rest framework and other third party apps django graphene

```bash
pip install djangorestframework django-filter djangorestframework-jwt graphene-django django-cors-headers django-graphql-auth django-graphql-jwt
```

### Add the installed third party apps to requirements.txt

```bash
pip freeze > requirements.txt
```

### Add the installed third party apps to settings.py

```python
# path ./hello/settings.py
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",

    # Third party apps

    'rest_framework',
    'rest_framework.authtoken',
    'django_filters',
    'corsheaders',
    'graphene_django',
    'graphql_auth',
    'graphql_jwt.refresh_token.apps.RefreshTokenConfig',

    # Local apps
    'contacts',
    'emails',
    'calendars',
    'notes',
    'tasks',
    'chats',
    'feeds',
    'trash',
]

```

### App is getting bigger so we need use linter and black formatter

```bash
pip install black flake8
```

### Add black and flake8 to requirements.txt

```bash
pip freeze > requirements.txt
```

### Create .flake8 file and add flake8 configurations

```bash
touch .flake8
```

```bash
# path ./.flake8

[flake8]
max-line-length = 120
exclude = .git,__pycache__,venv,settings.py,manage.py,apps/*/migrations/*,node_modules
```

### Create pyproject.toml file and add black configurations

```bash
touch pyproject.toml
```

```bash
# path ./pyproject.toml

[tool.black]
line-length = 120
target-version = ['py37']
include = '\.pyi?$'
exclude = '''
/(
    \.**git**
  | \.hg
  | \.mypy_cache
  | \.tox
  | \.venv
  | _build
  | buck-out
  | build
  | dist
  | venv
  | node_modules
  | settings.py
  | manage.py
  | apps/*/migrations/*
)/
'''
```