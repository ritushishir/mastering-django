- A industry-standard way to handle configuration, especially for sensitive data like passwords and secret keys.
- Keeps credentials out of your committed source code (Git), improving security and making your application easier to deploy across different environments (development, staging, production).

### Step-by-Step Guide to integrate Environment Variables for Database Settings

#### 1. Install `python-dotenv` package (if not already installed)

You can use the `python-dotenv` package to load environment variables from a `.env` file. Install it using pip:

```bash
pip install python-dotenv
```

#### 2. Create a `.env` file

Create a `.env` file in the root of your Django project (the same directory as `manage.py`).

Add your database credentials to this file:

```python
DB_NAME=geetshala
DB_USER=djangouser
DB_PASSWORD=djangopassword
DB_HOST=localhost
DB_PORT=3306
```

Add `.env` to your `.gitignore` file to prevent it from being committed to version control:

#### 3. Modify `settings.py` to use environment variables

a. Import the `os` module and `load_dotenv` function at the top of your `settings.py` file:

```python
# settings.py (At the very top)
import os
from pathlib import Path
from dotenv import load_dotenv

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent

# Load environment variables from .env file
load_dotenv(BASE_DIR / '.env')
```

b. Update the `DATABASES` setting to read from environment variables:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': os.getenv('DB_NAME'),
        'USER': os.getenv('DB_USER'),
        'PASSWORD': os.getenv('DB_PASSWORD'),
        'HOST': os.getenv('DB_HOST', 'localhost'),  # Default to localhost if not set
        'PORT': os.getenv('DB_PORT', '3306'),      # Default to 3306 if not set
    }
}
```
