# Middleware and Security

## Order of Middleware Classes {#order-of-middleware-classes}

The order of middleware classes in the `MIDDLEWARE` setting is crucial because each middleware processes the request and response in the order they are listed. For example, session middleware must come before authentication middleware to ensure that user sessions are available when authentication is processed.

```python
MIDDLEWARE = [
  'django.middleware.security.SecurityMiddleware',
  'django.contrib.sessions.middleware.SessionMiddleware',  # Must come before AuthenticationMiddleware   
  'django.contrib.auth.middleware.AuthenticationMiddleware',
  # ... other middleware ...
]
```

* Why order matters (e.g., Session before Authentication).
* How request and response objects flow through the stack.

## Security Best Practices {#security-best-practices}

* Using `SecurityMiddleware` for common security enhancements.
* Enforcing HTTPS with `SECURE_SSL_REDIRECT`.
* Setting secure cookies with `SESSION_COOKIE_SECURE` and `CSRF_COOKIE_SECURE`.

## CSRF Protection {#csrf-protection}

Django includes built-in protection against Cross-Site Request Forgery (CSRF) attacks. This is primarily handled by the `CsrfViewMiddleware`, which is included in the default middleware stack.

* How Django prevents Cross-Site Request Forgery.
* Using the `{% csrf_token %}` in forms and the `@csrf_exempt` decorator.
To protect your forms from CSRF attacks, include the `{% csrf_token %}` template tag within your HTML form:

```html
<form method="post">
  {% csrf_token %}
  <!-- form fields here -->
  <input type="submit" value="Submit">
</form>
```

For views that should be exempt from CSRF protection (e.g., certain API endpoints), you can use the `@csrf_exempt` decorator:

```python
from django.views.decorators.csrf import csrf_exempt
@csrf_exempt
def my_view(request):
  # View logic here
```
