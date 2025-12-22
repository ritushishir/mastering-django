# Advanced Django Admin

## The Zen of Admin {#the-zen-of-admin}

* Understanding the philosophy: The Admin is for internal staff, not end-users.
* When to use the Admin vs. when to build a custom dashboard.

## Customizing Admin Templates {#customizing-admin-templates}

* Overriding default Admin HTML for branding or functional tweaks.
* Utilizing the `admin/base_site.html` override.

## Creating Custom Admin Views {#creating-custom-admin-views}

* Adding completely new pages to the Admin interface.
* Mapping custom URLs within the `AdminSite` class.

## Overriding Built-in Views {#overriding-built-in-views}

* Customizing existing Admin views like the change list or detail view.
* Modifying the behavior of `add_view`, `change_view`, or `changelist_view`.
* Injecting additional context or altering form behavior.
