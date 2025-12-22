# Architecture and Deployment

## Shared Nothing {#shared-nothing}

* Understanding the "Shared Nothing" architecture for horizontal scaling.
* Managing state (sessions/media) outside the web server.

## Personal Preferences {#personal-preferences}

* Configuring settings for time zone, language, and static files.
* Organizing settings for different environments (Development vs. Production).

## Server Integration {#server-integration}

* Deploying Django applications with WSGI servers like Gunicorn or uWSGI.

* **Apache and mod_python:** Overview of the legacy deployment method.
* **FastCGI:** Using FastCGI for non-standard hosting environments.

*Note: Modern standards typically prefer WSGI (Gunicorn) or ASGI (Daphne/Uvicorn).

## Scaling and Performance Tuning {#scaling-and-performance-tuning}

* **Horizontal Scaling:** Adding more app servers behind a load balancer.
* **Performance Tuning:** Identifying bottlenecks with tools like Django Debug Toolbar.
* Caching strategies using Django's caching framework.
* Database optimization techniques, including indexing and query optimization.
* **Database Optimization:** Connection pooling and read-replicas.

