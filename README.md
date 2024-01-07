# Template-Django-PostgreSQL
Template: Django Backend with PostgreSQL Database

To get started, open a Terminal and run the following commands:

```python -m venv pyenv```
```.\pyenv\Scripts\Activate.ps1```
```pip install -r requirements.txt```

Make sure you have PostgreSQL installed from their website (https://www.postgresql.org/download/)

Open a psql terminal and press enter through the prompts with the details you chose during PostgreSQL installation (IP/Port/DB Name/Password). Typically you may press enter until you get to password.

In the psql prompt:

```CREATE DATABASE mydatabase;```
```GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;``` 

Typically myuser is ```postgresql```

cd to your project directory and run:

```django-admin startproject myproject```

Exit the prompt then go to your django project's ```settings.py``` file and enter this at the top level:

```python
from dotenv import load_dotenv

load_dotenv()
```

Then in the DATABASES section put this:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'mydatabase',
        'USER': 'postgres',
        'PASSWORD': f'{os.getenv("POSTGRESQL_PASSWORD")}',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

Create a ```.env``` file and enter ```POSTGRESQL_PASSWORD=your_sql_password```.

Run ```python manage.py migrate```

And ```python manage.py runserver```

You are good to go.