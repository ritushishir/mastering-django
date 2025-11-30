### Virtual Environment

A virtual environment is an isolated Python environment that allows you to manage dependencies for different projects separately. This helps avoid conflicts between packages required by different projects.

To create and activate a virtual environment, you can use the following commands:

```bash
python -m venv myenv
source myenv/bin/activate  # On Windows use `myenv\Scripts\activate`
```

- Try to run `django-admin --version` to check if Django is installed in your virtual environment.
- If Django is not installed, you can install it using pip:

```bash
pip install django
```
