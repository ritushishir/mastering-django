## Concpet of Django Project and App

- In Django, a **Project** is the entire web application, while an **App** is a modular component that serves a specific functionality within that project.

#### 🏗️ The Analogy: A Shopping Mall and Stores

| Component         | Django Equivalent | Description                                                                                                                          |
| ----------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| The Shopping Mall | Project           | The entire website (e.g., your album site, artist site). It contains the overall configuration and settings that apply to everything |
| Individual Store  | App               | A self-contained feature (e.g., a "Users" store, a "Album" store, a "Artist" store). It handles a specific function                  |
| Mall Directory    | urls.py           | The main routing map that directs a visitor to the correct Store (App)                                                               |
| Mall Rules/Lease  | settings.py       | The core configuration (database, security, time zone) that all Stores must follow"                                                  |

### 🏛️ The Project (geetshala/ or config/)

The Django Project is the encompassing configuration for your entire web application.

#### Key Characteristics

- **Configuration Hub**: It holds the global settings in settings.py (database connection, security keys, installed apps, middleware).

* **Single Entry Point**: It defines the main URL routing in urls.py, which acts as the master table of contents for the entire site.

* **One per web application**: You typically have only one Project for a single deployed website.

* **Management**: Contains manage.py, the script used to run commands (like runserver and migrate) for the entire project structure.

??? tip "Mini-Challenge: What if you change the database configuration in settings.py?"

    If you change the database in settings.py, every App in the project uses that new database.

### 🧩 The App (songs/ or users/)

A Django App is a self-contained module that handles a single, specific functionality. Apps are designed to be reusable.

#### Key Characteristics

- **Specific Functionality**: An App focuses on one thing (e.g., handling user registration, displaying songs posts, managing genre list).

- **MVT Components**: Each App contains its own Models, Views, and Templates related to its function.

- **Reusability**: A well-written App can be packaged up and dropped into other Django Projects. For instance, a "Ratings" app could be used for a artists project, or a songs project.
- **Independence**: It has its own urls.py, models.py, views.py, etc.

### 🔄 How They Interact

**Request Arrives** --> **Project Routes** --> **App Handles** --> **App Executes**

**Advantages**

- Modular approach
- Scalability and Maintainability

??? tip "Mini-Challenge: Relevant apps for the Geetshala Project"

    Possible apps could include:

    * users - user authentication and profiles
    * artists - for managing artist data
    * songs - for managing song data
    * playlists - for creating and managing playlists
    * reviews - for user reviews and ratings
    * api - for exposing RESTful endpoints

#### Let's Make Our Hands Dirty

??? tip "Mini-Challenge: Create a New App Called 'Songs'"

    Check the available commands in manage.py by running and use the appropriate one to create a new app named `songs`.

- A new directory `songs/` with the following structure

```plaintext
geetshala/
manage.py
songs/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

??? tip "Mini-Challenge: What Next After Creating the App?"

    How do the Project and App interact? How does the **Project** delegate tasks to the **Apps**?
