# Django Security, State, and Performance

## 1. Sessions and State Management

### [Django’s Session Framework](/docs/unit-4/session-and-state-management#djangos-session-framework-session-framework)

* Configuring session engines (Database, Cache, File-based, or Cookie-based).
* How to store and retrieve persistent data for anonymous and logged-in users.

---

## 2. Authentication and Authorization

### [Users and Authentication](/docs/unit-4/authentication-and-authorization#users-and-authentication)

* Managing user logins, logouts, and password hashing.
* Using the built-in `User` model.

### [Permissions](/docs/unit-4/authentication-and-authorization#permissions)

Restricting access to views based on user rights

### [Groups](/docs/unit-4/authentication-and-authorization#groups)

Organizing users for bulk permission management

### [Messages](/docs/unit-4/authentication-and-authorization#messages)

Using the Messages Framework for one-time notifications (e.g., "Login Successful").

### [Profiles](/docs/unit-4/authentication-and-authorization#profiles)

Extending user data with Custom User Models or Profile linked models.

---

## 3. The Caching Framework

### [Setting Up the Cache](/docs/unit-4/setting-up-caching#setting-up-the-cache)

* Choosing a backend: Memcached, Redis, Database, or Local-memory.

### [The Per-Site Cache](/docs/unit-4/setting-up-caching#per-site-cache)

* Enabling the "fetch" and "update" middleware to cache the entire website automatically.

### [The Per-View Cache](/docs/unit-4/setting-up-caching#per-view-cache)

* Using the `@cache_page` decorator to cache specific, expensive views.

### [The Low-Level Cache API](/docs/unit-4/setting-up-caching#low-level-cache-api)

* Manually setting, getting, and deleting keys in the cache for granular control.

### [Upstream Caches](/docs/unit-4/setting-up-caching#upstream-caches)

* Working with Nginx/Varnish and the `Vary` header for proxy caching.

### [Other Optimizations](/docs/unit-4/setting-up-caching#other-optimizations)

* Database indexing, `select_related`, and `prefetch_related` to reduce query overhead.

---

## 4. Middleware and Security

### [Order of Middleware Classes](/docs/unit-4/middleware-and-security#order-of-middleware-classes)

* Why order matters (e.g., Session before Authentication).
* How request and response objects flow through the stack.

### [Security Best Practices](/docs/unit-4/middleware-and-security#security-best-practices)

### [CSRF Protection](/docs/unit-4/middleware-and-security#csrf-protection)

* How Django prevents Cross-Site Request Forgery.
* Using the `{% csrf_token %}` in forms and the `@csrf_exempt` decorator.

---

## 5. The Django Standard Library (Contrib Apps)

### [Sites](/docs/unit-4/django-standard-library#sites)

* Managing multiple websites from a single Django installation.

### [Flatpages](/docs/unit-4/django-standard-library#flatpages)

* Creating simple, static-like pages (e.g., "About Us", "Privacy Policy") via the Admin interface.

### [Redirects](/docs/unit-4/django-standard-library#redirects)

* Managing 301 and 302 redirects within the database.

### [Humanizing Data](/docs/unit-4/django-standard-library#humanizing-data)

* Using `django.contrib.humanize` to turn numbers/dates into readable strings (e.g., "3 days ago", "1.2 million").

### [Markup Filters](/docs/unit-4/django-standard-library#markup-filters)

* Processing text as Markdown, ReStructuredText, or other formats within templates.
