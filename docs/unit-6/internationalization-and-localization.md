# Internationalization and Localization

## Specifying Translation Strings in Python Code {#specifying-translation-strings-in-python-code}

* Using `gettext` and `gettext_lazy`.
* Handling pluralization in Python logic.

## Specifying Translation Strings in Template Code {#specifying-translation-strings-in-template-code}

* Using the `{% trans %}` and `{% blocktrans %}` tags.
* Translating variable content within templates.

## Creating Language Files {#creating-language-files}

* Working with `.po` (Portable Object) and `.mo` (Machine Object) files.
* Using `makemessages` and `compilemessages` commands.

## Language Preference Discovery {#language-preference-discovery}

* How Django determines the user's language via URL, Cookies, or Browser headers.
* The role of `LocaleMiddleware`.

## The "set_language" Redirect View {#the-set_language-redirect-view}

* Implementing a language switcher for users to manually toggle between languages.

## Using Translations in Projects {#using-translations-in-projects}

* Structuring the `locale/` directory.
* Best practices for maintaining multi-lingual content.

## Translations and JavaScript {#translations-and-javascript}

* Using the `javascript_catalog` view to make translation strings available in frontend scripts.
