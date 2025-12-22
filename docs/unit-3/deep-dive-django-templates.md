# Deep Dive - Django Template System

## Template Language Review {#template-language-review}

* Quick refresh on Tags, Filters, and Variables.
* Inheritance strategies (`{% extends %}` and `{% block %}`).

## Request Context and Context Processors {#request-context-and-context-processors}

* Understanding `RequestContext` vs. `Context`.
* Configuring built-in and custom context processors to make data available globally across templates.

## Inside Template Loading {#inside-template-loading}

* How Django finds your HTML files.
* The `DIRS` and `APP_DIRS` configurations.

## Extending the Template System {#extending-the-template-system}

* Writing Custom Template Tags (`simple_tag`, `inclusion_tag`).
* Creating Custom Template Filters.

## Writing Custom Template Loaders {#writing-custom-template-loaders}

* Loading templates from non-standard sources (e.g., Database or API).

## Using the Built-in Template Reference {#using-the-built-in-template-reference}

* Leveraging the Django admin documentation for template tags and filters.

## Configuring the Template System in Standalone Mode {#configuring-the-template-system-in-standalone-mode}
