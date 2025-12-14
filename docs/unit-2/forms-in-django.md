# 📝 Forms in Django

Django's form handling is one of its most powerful and utilized features. It abstracts away the tedious and often insecure process of preparing data for rendering, validating user-submitted data, and converting it to Python data types.

The core components of the Django form system are:

- **Form Class**:

  The primary class used to define a form, specifying the fields and their validation rules.

- **Field Objects**:

  Instances of classes like CharField, IntegerField, etc., which handle validation and cleaning for specific data types.

- **Widget Objects**:

  Define how a form field is rendered as an HTML input type (e.g., `<input type="text">`, `<textarea>`, `<select>`). Widgets are purely concerned with the presentation layer.

## Why use Django Forms?

- **Security**:

  Forms handle CSRF (Cross-Site Request Forgery) protection automatically and help prevent other common web vulnerabilities by sanitizing and validating input.

- **Convenience**:

  They automate rendering HTML, displaying error messages, and repopulating forms after an invalid submission.

- **Validation**:
  
  Built-in validation methods for common data types (e.g., email, URL, date) and the ability to define custom validation rules.

- **Integration with Models**:

  ModelForms allow for easy creation of forms directly tied to Django models, reducing boilerplate code for CRUD operations.

- **Data Cleaning**:

  The system ensures that data is converted into reliable Python types (e.g., a string from a text field becomes a Python int for an IntegerField).

## ✨ The Perfect Form

The Perfect Form" often refers to a form that is secure, fully validated, and provides an excellent user experience (UX).

**Key Characteristics:**

- **HTML Structure**:

  The form is correctly wrapped in `<form>` tags with the proper method (usually POST) and includes the CSRF token ({% csrf_token %}).

- **Validation**:
  
  It enforces both field-level (e.g., is this a valid email?) and form-level (e.g., does password match confirm password?) validation.

- **Clear Errors**:

  Validation errors are displayed next to the relevant field, making it easy for the user to correct their input.

- **Accessibility**:

  Use of proper HTML labels and accessibility attributes.

- **Repopulation**:

  If a form submission fails validation, the form is re-rendered with the user's previously entered data to prevent them from having to re-type everything.

## 🧱 Two Types of Forms in Django

### Standard Forms (`forms.Form`)

  Used for forms that do not directly interact with a database model. You define each field manually.

### Model Forms (`forms.ModelForm`)

  Automatically create a form based on a Django model. This is useful for creating forms that correspond to database records.

## Standard Form Example: Feedback Form

### Defining a Standard Form

- define every field explicitly in the `forms.py` file.

```python
from django import forms
class FeedbackForm(forms.Form):
  # This form does not interact with a database model directly.
  name = forms.CharField(
    label='Your Name',
    max_length=100
  )
  email = forms.EmailField(
    label='Your Email',
    required=True
  )
  message = forms.CharField(
    label='Your Feedback',
    widget=forms.Textarea(attrs={'rows': 5, 'cols': 40, 'placeholder': 'Enter your feedback here...'}) 
  )

  def clean_name(self):
      name = self.cleaned_data.get('name')
      if any(char.isdigit() for char in name):
          raise forms.ValidationError("Name cannot contain numbers.")
      return name
  
  def clean_message(self):
      message = self.cleaned_data.get('message')
      if len(message) < 10:
          raise forms.ValidationError("Message must be at least 10 characters long.")
      return message
```

### Rendering the Form in a Template

- Render the defined form in `feedback.html`

```html
<h1>Please provide your feedback below</h1>
{% if form.errors %}
<ul>
  {% for field in form %}
  {% for error in field.errors %}
  <li>{{ error }}</li>
  {% endfor %}
  {% endfor %}
</ul>
{% endif %}
<form method="post" action="">
  {% csrf_token %}
  {{ form.as_p }}    
  <button type="submit">Submit Feedback</button>
</form>
```

### Creating a URL for the Form View

- add a URL pattern in `urls.py` to point to the form view

```python
# feedback/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.feedback_view, name='feedback'),
]

# geetshala/urls.py
.....
.....
urlpatterns = [
    ......
    path('feedback/', include('feedback.urls')),
]
```

### Procesing the Form in Views

- view logic to handle both the initial loading and form submission in `views.py`

```python
from django.http import HttpResponse
from django.shortcuts import render, redirect
from .forms import FeedbackForm
def feedback_view(request):
  if request.method == 'POST':
    form = FeedbackForm(request.POST)
    if form.is_valid():
      # Process the cleaned data
      name = form.cleaned_data['name']
      email = form.cleaned_data['email']
      message = form.cleaned_data['message']
      # e.g. send email
      print(f"Feedback received from {name} ({email}): {message}")
      return HttpResponse("Thank you for your feedback!")  # Simply render a thank you message
    else:
      # Form is invalid; render the form with error messages
      return render(request, 'feedback.html', {'form': form})
  else:
    form = FeedbackForm()  # Unbound form for GET request

  return render(request, 'feedback.html', {'form': form})
```

??? tip "Do It Yourself: Create a New Form to collect Feedback on the page"

    Create an endpoint with the form to collect feedback from users about the website. The form should include fields for name, email, and message. Implement validation to ensure that the email is valid and the message is at least 10 characters long. Render the form in a template and handle form submissions in a view.

## ✍️ Model Form Example: Song Submission Form

- `ModelForm` is a convenience class that drastically simplifies the creation of forms that interact directly with a Django model.

- The `ModelForm` is a powerful abstraction that allows you to focus on your application's logic rather than the repetitive task of defining form fields.

It handles:

**Field Definition**: Automatically creates form fields corresponding to the model's fields (e.g., a CharField for a TextField, an EmailField for an EmailField).

**Initial Data**: Pre-populates the form with data from an existing model instance (when editing).

**Saving Data**: Automatically calls the model's save() method upon valid submission.
Basic `ModelForm` Example

### Define the Form in forms.py

This code defines a form in `songs/forms.py` based on the `Song` model.

```python
from django import forms
from .models import Song
class SongForm(forms.ModelForm):
  """
  Creates a form based on the Song model.
  """
  class Meta:
      # Specify the model to base the form on
      model = Song
      
      # Specify the fields to include in the form
      fields = ['title', 'lyrics', 'released_date', 'is_published']

      # Optional customization
      # Add custom labels for the fields
      labels = {
          'title': 'Title of the Song',
          'lyrics': 'Lyrics',
          'released_date': 'When was it released?',
          'is_published': 'Should this song be in the portal?',
      }

      # Optional customization of widgets
      widgets = {
          'lyrics': forms.Textarea(attrs={'rows': 5, 'cols': 40}),
          'released_date': forms.SelectDateWidget(),
      }
```

### Using the `SongForm` in a View

In your view, you can instantiate the `SongForm`, render it in a template, and handle form submissions.

```pythonpython
from django.shortcuts import render, redirect
from .forms import SongForm
def create_song(request):
  if request.method == 'POST':

    # Bind the POST data to the form
    form = SongForm(request.POST)

    if form.is_valid():
      form.save()  # Saves the new Song instance to the database
      return redirect('song_list')  # Redirect to a list of songs or another page

  else:
    form = SongForm()  # Unbound form for GET request

  return render(request, 'song_form.html', {'form': form})
```

### Render the Form in a Template

In the template, you can render the form fields automatically using the `as_p`, `as_ul`, or `as_table` methods, or manually for more control.

```html
<h2>Submit a New Song</h2>
<form method="post">
  {% csrf_token %}
  {{ form.as_p }}    
  <button type="submit">Submit Song Details</button>
</form>
```

### Creating a URL for the ModelForm View

- add a URL pattern in `urls.py` to point to the form view

```python
# songs/urls.py
...

urlpatterns = [
    path('new', views.create_song, name='create_song'),
    ....
]
```

??? tip "Do It Yourself: Add a page to update the Song details"

    Create a view and template to update existing Song records using the `SongForm` ModelForm. Ensure that the form is pre-populated with the current data of the song being edited. Handle form submissions to save the updated data back to the database.

## 🔒 Custom Validation Rules

You can define custom rules for individual fields or rules that depend on multiple fields.

### Field-Level Validation

  You can add a `clean_<fieldname>` method to your form class. This method is executed after the field's default validation and cleaning.

```python
def clean_title(self):
  title = self.cleaned_data.get('title')
  if title and (len(title) < 5):
    raise forms.ValidationError("Title must be at least 5 characters long")
  return title
```

### Form-Level Validation

  For rules that involve comparing or checking multiple fields (e.g., ensuring a start_date is before an end_date), you use the main `clean()` method.

```python
def clean(self):
  cleaned_data = super().clean()
  title = cleaned_data.get('title')
  lyrics = cleaned_data.get('lyrics')
  if title and lyrics and title in lyrics:
    raise forms.ValidationError("Title do not match with the lyrics content.")
```

## 🎨 Custom Look and Feel

Django provides powerful ways to customize the appearance of your forms without giving up its validation benefits.

### Using Custom Widgets

Widgets control the HTML input element. You can override the default widget for any field.

```python
message = forms.CharField(widget=forms.Textarea(attrs={'class': 'form-control custom-textarea', 'rows': 5}), label='Your Feedback')
```

### Manual Rendering

For maximum control, you can render each field individually in your template:

```html
<div class="form-group">
  {{ form.subject.label_tag }} {{ form.subject }} {% for error in form.subject.errors %}
    <p class="error-message">{{ error }}</p>
  {% endfor %}
</div>
```

### Template Packs (Recommended)

Modern Django encourages using form template packs (or template fragment overrides since Django 3.2). This involves overriding the default HTML snippets that Django uses to render forms (`{{ form.as_p }}`). Libraries like `django-crispy-forms` are popular for applying CSS frameworks (like Bootstrap) easily.
