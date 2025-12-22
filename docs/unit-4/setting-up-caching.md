
# Caching

Django's caching framework helps improve the performance of your web applications by storing frequently accessed data in a fast storage layer. This reduces the need to repeatedly fetch data from the database or perform expensive computations.

## Setting Up the Cache {#setting-up-the-cache}

To set up caching in your Django project, you need to choose a caching backend. Common options include Memcached, Redis, database caching, or local-memory caching. You can configure the cache backend in your `settings.py` file using the `CACHES` setting. For example, to use Memcached:

```python
CACHES = {
  'default': {
    'BACKEND': 'django.core.cache.backends.memcached.MemcachedCache',
    'LOCATION': '127.0.0.1:11211',
  }
}
```

## The Per-Site Cache {#per-site-cache}

The per-site cache allows you to cache the entire site by enabling the `FetchFromCacheMiddleware` and `UpdateCacheMiddleware` in your `MIDDLEWARE` settings. This caches all pages automatically.

```python
MIDDLEWARE = [
  'django.middleware.cache.UpdateCacheMiddleware',
  # ... other middleware ...
  'django.middleware.cache.FetchFromCacheMiddleware',
]
```

## The Per-View Cache {#per-view-cache}

You can cache specific views using the `@cache_page` decorator. This is useful for caching expensive views that don't change often.

```python
from django.views.decorators.cache import cache_page
@cache_page(60 * 15)  # Cache for 15 minutes
def my_expensive_view(request):
  # View logic here
```

## The Low-Level Cache API {#low-level-cache-api}

Django provides a low-level cache API that allows you to manually set, get, and delete cache entries. You can use the `cache` object from `django.core.cache`.

```python
from django.core.cache import cache
# Set a value in the cache
cache.set('my_key', 'my_value', timeout=300)  # Expires in
# Get a value from the cache
value = cache.get('my_key')
# Delete a value from the cache
cache.delete('my_key')
```

## Upstream Caches {#upstream-caches}

When using upstream caches like Nginx or Varnish, you can control caching behavior with the `Vary` header. This header tells the cache to store different versions of a resource based on certain request headers (e.g., `Accept-Language`, `User-Agent`).

```python
from django.views.decorators.vary import vary_on_headers
@vary_on_headers('User-Agent')
def my_view(request):
  # View logic here
```

## Other Optimizations {#other-optimizations}

In addition to caching, you can optimize database queries using techniques like indexing, `select_related`, and `prefetch_related`. These methods help reduce the number of database queries and improve performance.

```python
# Using select_related to fetch related objects in a single query
books = Book.objects.select_related('author').all()
# Using prefetch_related to fetch many-to-many relationships efficiently
authors = Author.objects.prefetch_related('books').all()
```

By implementing caching and optimizing database access, you can significantly enhance the performance of your Django applications.
