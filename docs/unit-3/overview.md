# Advanced Concepts in URL Dispatching, View and Template System

## 1. Advanced URL Dispatching

### URLconf Tricks

* Naming patterns for easier reverse lookups.
* Passing extra options to view functions.
* Handling complex regex/path converters for cleaner URLs.

---

## 2. Working with Generic Views

### [Class-Based Views vs. Function-Based Views](/docs/unit-3/working-with-generic-views#cbvs-and-fbvs)

### [Using Generic Views](/docs/unit-3/working-with-generic-views#using-generic-views)

### [Generic Views of Objects](/docs/unit-3/working-with-generic-views#generic-views-of-objects)

### [Extending Generic Views](/docs/unit-3/working-with-generic-views#extending-generic-views)

---

## 3. Deep Dive: Django Template System

### Template Language Review

* Quick refresh on Tags, Filters, and Variables.
* Inheritance strategies (`{% extends %}` and `{% block %}`).

### Request Context and Context Processors

* Understanding `RequestContext` vs. `Context`.
* Configuring built-in and custom context processors to make data available globally across templates.

### Inside Template Loading

* How Django finds your HTML files.
* The `DIRS` and `APP_DIRS` configurations.

### Extending the Template System

* Writing Custom Template Tags (`simple_tag`, `inclusion_tag`).
* Creating Custom Template Filters.

### Writing Custom Template Loaders

* Loading templates from non-standard sources (e.g., Database or API).

### Using the Built-in Template Reference

* Leveraging the Django admin documentation for template tags and filters.

### Configuring the Template System in Standalone Mode

* Using the Django Template Engine in non-Django Python scripts.

---

## 4. Specialized Content & Outputs

### The Basics: Views and MIME-types

* Changing the `content_type` of a response.
* How browsers interpret different MIME types.

### Producing CSV

* Generating dynamic spreadsheet exports using the `csv` Python module.

### Generating PDFs

* Integrating libraries like `ReportLab` or `WeasyPrint` to render PDF documents.

### Other Possibilities

* Generating JSON responses for APIs.
* Creating dynamic ZIP files or images.

---

## 5. Metadata & Discovery Frameworks

### The Syndication Feed Framework

* Creating RSS and Atom feeds for your site content.

### The Sitemap Framework

* Generating `sitemap.xml` to assist search engines in indexing your site.
