# Django Globalisation, Security, and Scalability

## Internationalization (i18n) and Localization (l10n)

### [Specifying Translation Strings in Python Code](/docs/unit-6/internationalization-and-localization#specifying-translation-strings-in-python-code)

* Using `gettext` and `gettext_lazy`.
* Handling pluralization in Python logic.

### [Specifying Translation Strings in Template Code](/docs/unit-6/internationalization-and-localization#specifying-translation-strings-in-template-code)

* Using the `{% trans %}` and `{% blocktrans %}` tags.
* Translating variable content within templates.

### [Creating Language Files](/docs/unit-6/internationalization-and-localization#creating-language-files)

* Working with `.po` (Portable Object) and `.mo` (Machine Object) files.
* Using `makemessages` and `compilemessages` commands.

### [Language Preference Discovery](/docs/unit-6/internationalization-and-localization#language-preference-discovery)

* How Django determines the user's language via URL, Cookies, or Browser headers.
* The role of `LocaleMiddleware`.

### [The "set_language" Redirect View](/docs/unit-6/internationalization-and-localization#the-set_language-redirect-view)

* Implementing a language switcher for users to manually toggle between languages.

### [Using Translations in Projects](/docs/unit-6/internationalization-and-localization#using-translations-in-projects)

* Structuring the `locale/` directory.
* Best practices for maintaining multi-lingual content.

### [Translations and JavaScript](/docs/unit-6/internationalization-and-localization#translations-and-javascript)

* Using the `javascript_catalog` view to make translation strings available in frontend scripts.

---

## Advanced Web Security

### [Web Security Themes](/docs/unit-6/advanced-web-security#web-security-themes)

* The philosophy of "Defense in Depth."

### [Common Vulnerabilities & Mitigations](/docs/unit-6/advanced-web-security#common-vulnerabilities-and-mitigations)

* **SQL Injection:** How the Django ORM protects against malicious queries.
* **XSS (Cross-Site Scripting):** Automatic HTML escaping in templates.
* **CSRF (Cross-Site Request Forgery):** Token validation for state-changing requests.
* **Session Forging/Hijacking:** Securing session cookies and rotating IDs.
* **Email Header Injection:** Preventing attackers from using your contact forms for spam.
* **Directory Traversal:** Protecting file uploads and media serving.

### [Exposed Error Messages](/docs/unit-6/advanced-web-security#exposed-error-messages)

* The danger of `DEBUG = True` in production.
* Customizing 404 and 500 error pages.

---

## Architecture and Deployment

### [Shared Nothing](/docs/unit-6/architecture-and-deployment#shared-nothing)

* Understanding the "Shared Nothing" architecture for horizontal scaling.
* Managing state (sessions/media) outside the web server.

### [Personal Preferences](/docs/unit-6/architecture-and-deployment#personal-preferences)

* Organizing settings for different environments (Development vs. Production).

### [Server Integration](/docs/unit-6/architecture-and-deployment#server-integration)

* **Apache and mod_python:** Overview of the legacy deployment method.
* **FastCGI:** Using FastCGI for non-standard hosting environments.

### [Scaling and Performance Tuning](/docs/unit-6/architecture-and-deployment#scaling-and-performance-tuning)

* **Horizontal Scaling:** Adding more app servers behind a load balancer.
* **Performance Tuning:** Identifying bottlenecks with tools like Django Debug Toolbar.
* **Database Optimization:** Connection pooling and read-replicas.

---

## Monitoring and Maintenance

### [Importance of Monitoring](/docs/unit-6/monitoring-and-maintenance#importance-of-monitoring)

### [Monitoring Tools and Techniques](/docs/unit-6/monitoring-and-maintenance#monitoring-tools-and-techniques)

### [Routine Maintenance Tasks](/docs/unit-6/monitoring-and-maintenance#routine-maintenance-tasks)

### [Performance Optimization](/docs/unit-6/monitoring-and-maintenance#performance-optimization)

### [Backup and Disaster Recovery](/docs/unit-6/monitoring-and-maintenance#backup-and-disaster-recovery)

### [Documentation and Knowledge Sharing](/docs/unit-6/monitoring-and-maintenance#documentation-and-knowledge-sharing)

### [Security Audits and Compliance](/docs/unit-6/monitoring-and-maintenance#security-audits-and-compliance)

### [User Feedback and Continuous Improvement](/docs/unit-6/monitoring-and-maintenance#user-feedback-and-continuous-improvement)
