# Lionheart-Core Internal Documentation

Lionheart-Core is the main repository that houses the Lionheart web application. 
Please follow these standard practices when working on the Lionheart repository. 

## Installation

The 'development' branch will house all development activity. **NEVER** push to the master branch. 

The development branch will automatically deploy on our Heroku server as soon as it detects new pushes. Please ensure that the server is in a deployable state before pushing anything.  

Be VERY careful when pushing updates to the development branch, especially anything affecting the following files (in any directory):
- views.py
- urls.py
- settings.py


## Documentation

> Table of Contents
> 1. [Application Structure](## Application Structure)
> 2. [Settings.py](##)
> 3. [Creating New Pages](##)
> 4. [Linking Static Content](##)
> 5. [Deploying to Heroku](##)

### Application Structure
---
The lionheart-core web application is structured as follows: 
```bash
├── dash
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── landing_page
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── static
│   │   ├── css
│   │	│	├── <style.css files>
│   │   ├── fonts
│   │	│	├── <static font files>
│   │   ├── img
│   │	│	├── <static img files>
│   │   └── js
│   │	│	├── <static javascript goes here>
│   ├── templates
│   │   └── landing_page
│   │       ├── * index.html    *
│   │       ├── * plans.html    *
│   │       └── * register.html *
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── lionheart
│   ├── | settings.py |
│   ├── | urls.py     |
│   └── wsgi.py
├── manage.py
├── requirements.txt
├── templates
│   └── registration
│       ├── * login.html  *
```
```text
< >  = STATIC
| |  = IMPORTANT -- BE CAREFUL
* *  = TEMPLATES 
```

While the application structure may appear confusing at first, it is actually relatively simple. 

At the top level we have the 'app' folders, which include:

'dash' (Housing the views, templates, and logic for our main application), 

'landing_page' (Housing views and templates for: registration page, home page, ALL static pages before being authorized {logged in}. 

> Auth logic is housed within the 'landing_page' directory, however **auth templates are stored in templates/registration/**).

### Settings.py
---
### Creating New Pages
---
Creating new pages within the application requires a few more steps than simply adding HTML/CSS and linking the files together. 

1. **Creating the template**
Create an HTML template, include the following at the very top of the file: 

```HTML
<!doctype html>
{% load static %}
```

This tells the Django/WhiteNoise to load the contents of the static folder, allowing us to implement custom css, fonts, static images, etc. without loading the static you will be greeted with an error page reminding you to add this line. 

Once the template has been created/fleshed out save it in the 'app'/templates/'app'/ directory – Where 'app' = landing_page, dash, etc.

2. **Creating the URL routing**

Open lionheart/urls.py and **ADD** the following line to the 'urlpatterns' dict
```python
urlpatterns = [
	...
    path('PATH_URL/', include('APP_NAME.urls')),
]
```
> Where 'PATH_URL' = Link in browser, for example: www.lionheart.com/login = login/
>
> Where APP_NAME = Name of app where template is located, for example: 'landing_page' or 'dash'

Edit APP_NAME/urls.py and add the following:

```python
urlpatterns = [
    ...
    path('PATH_URL', views.PATH_URL, name='PATH_URL'),
]
```
> Where PATH_URL = PATH_URL from previous step.

Now open APP_NAME/views.py and add:

```python
def PATH_URL(request):
	return render(request, 'APP_NAME/TEMPLATE_NAME.html')
```
> Where APP_NAME = subdirectory that templates are stored in (i.e. landing_page/templates/landing_page/ ...)
>
> This function defines the URL request and renders the template using the Jinja2 templating engine.

Now when you visit app_url.com/PATH_URL Django will check the lionheart/urls.py file, where it will be sent to APP_NAME.urls (for instance, landing_page/urls.py. At that point it will look for PATH_URL, which will tell Django to render views.PATH_URL).

### Linking Static Content
---

COMING SOON


### Deploying to Heroku
---

Simply push to the 'development' branch and Heroku will automtically redeploy the server. 

> Make sure the build is deployable locally **before** deploying to Heroku, else it will result in a build failure.
 
The staging (dev) server located at:

>[Lionheart Dev Server](lionheart-core-dev.herokuapp.com)





