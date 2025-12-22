# Middleware Architecture

## Middleware Overview {#middleware-overview}

* Understanding the request/response lifecycle.
* How Middleware acts as a "hook" system for Django’s input and output.

## Middleware Installation {#middleware-installation}

* Configuring the `MIDDLEWARE` setting in `settings.py`.
* Understanding the importance of plugin order.

## Middleware Methods {#middleware-methods}

* Defining custom logic using `__call__`.
* Hooking into specific stages: `process_view`, `process_exception`, and `process_template_response`.

## Built-in Middleware {#built-in-middleware}

* Deep dive into essential defaults: `CommonMiddleware`, `SecurityMiddleware`, and `GZipMiddleware`.
