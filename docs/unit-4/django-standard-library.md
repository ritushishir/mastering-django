# The Django Standard Library (Contrib Apps)

Django comes with a rich set of built-in applications, known as "contrib apps," that provide common functionalities needed in web development. These apps can be easily integrated into your Django projects to save time and effort.

## Sites {#sites}

The Sites framework allows you to manage multiple websites using a single Django installation. Each site can have its own domain name and content.

* How to configure and use the Sites framework.
* Use cases for multi-site management.

## Flatpages {#flatpages}

Flatpages is a simple way to manage static content on your site without needing a full CMS. It allows you to create and edit static pages through the Django admin interface.

* Creating and managing flatpages via the Admin.

* Linking flatpages to URLs in your project.

## Redirects {#redirects}

The Redirects framework helps you manage URL redirections within your Django application. This is useful for maintaining SEO when URLs change or for redirecting old links to new ones.

* Setting up and managing redirects in the Admin.
* Common scenarios for using redirects (e.g., 301 and 302 redirects).
* How to configure the Redirects framework in your project.

```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',  # Must come before AuthenticationMiddleware
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.redirects.middleware.RedirectFallbackMiddleware',  # Enables Redirects framework
    # ... other middleware ...
]
```

## Humanizing Data {#humanizing-data}

Django's `django.contrib.humanize` app provides template filters that help you present data in a more human-readable format. This includes formatting numbers, dates, and times in a way that is easier for users to understand.

* Using humanize filters in templates (e.g., `naturaltime`, `intcomma`).
* Examples of humanized data presentation.

```html
{{ some_date|naturaltime }}  <!-- e.g., "3 days ago" -->
{{ some_number|intcomma }}    <!-- e.g., "1,234,567" -->
```

### Markup Filters {#markup-filters}

Django provides several markup filters that allow you to process text in different formats directly within your templates. These filters can convert plain text into HTML using various markup languages.

* Common markup filters: `markdown`, `restructuredtext`, `linebreaks`, `linebreaksbr`.

```html
{{ some_markdown_text|markdown }}
{{ some_restructuredtext|restructuredtext }}
{{ some_text|linebreaks }}
{{ some_text|linebreaksbr }}
```

* How to enable and use these filters in your templates.
* Examples of using markup filters for content formatting.

```python
INSTALLED_APPS = [
    # ... other installed apps ...
    'django.contrib.sites',
    'django.contrib.flatpages',
    'django.contrib.redirects',
    'django.contrib.humanize',
    # ... other installed apps ...
]
```
