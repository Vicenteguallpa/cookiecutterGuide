# cookiecutterGuide
This guide begins where [Writing your first Django app, part 7](https://docs.djangoproject.com/en/2.2/intro/tutorial07/) left off. Assuming you used the same directory and file names that were used in the "Writing your first Django app tutorial," your project structure in Atom should look somewhat like the following: 

mysite/  
&nbsp;&nbsp;&nbsp;&nbsp;mysite/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_pycache__/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;settings.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;urls.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;wsgi.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;settings.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;urls.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;wsgi.py  
&nbsp;&nbsp;&nbsp;&nbsp;polls/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_pycache__/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;admin.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;apps.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;models.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tests.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;urls.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;views.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;migrations/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_pycache__/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0001_initial.cpython-37.pyc  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0001_initial.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;static/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;polls/   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;images/   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;background.gif  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;style.css  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;templates/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;polls/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;detail.html  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;index.html  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;results.html  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\_\_init__.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;admin.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;apps.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;models.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;tests.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;urls.py  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;views.py  
&nbsp;&nbsp;&nbsp;&nbsp;templates/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;admin/  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;base_site.html  
&nbsp;&nbsp;&nbsp;&nbsp;db.sqlite3  
&nbsp;&nbsp;&nbsp;&nbsp;manage.py

## Prerequisites & Assumptions
As mentioned before, this project utilizes the same directory and file names as in the tutorial. You should already have Atom and docker installed.

## Guide
Open your git bash or terminal. Now change over to the directory that contains the upper "mysite" directory. You should have the following:
```
$ ls
mysite/
```
Install CookieCuteter:
```
$ pip install "cookiecutter>=1.4.0"
```
Now run it against the following repo:
```
$ cookiecutter https://github.com/pydanny/cookiecutter-django
```
You'll be prompted for some values. Provide them as follows 
* project_name: mysite_cookiecutter
* project_slug: mysite_cookiecutter
* description: inserting my first Django app into the cookiecutter template
* author_name: [YOUR NAME HERE]
* domain_name: mysite.com
* email: [YOUR EMAIL HERE]
* version: 0.0.1
* Select open_source_license: 1
* timezone: America/New_York
* windows: yes 
* use_pycharm: no
* use_docker: yes
* Select postgresql_version: 1
* Select js_task_runner: 2
* Select cloud_provider: 1
* custom_bootstrap_compilation: no
* use_compressor: no
* use_celery: no
* use_mailhog: no
* use_sentry: no
* use_whitenoise: yes
* use_heroku: no
* use_travisci: no
* keep_local_envs_in_vcs: no
* debug: no

You should now see a "[SUCCESS]: Project initialized, keep up the good work!" message and your directory should now contain "mysite_cookiecutter" directory
```
$ ls
mysite/ mysite_cookiecutter/
```
Now copy the "polls" directory thats within the upper "mysite" directory into the "mysite_cookiecutter" directory: 
```
$ cd mysite/
$ ls 
db.sqlite3 manage.py* mysite/ polls/ templates/
$ cp -r polls/ ../mysite_cookiecutter
```
You should now have the "polls" directory inside the "mysite_cookiecutter" directory.  
Now open the "mysite_cookiecutter" project folder in Atom. In Atom, open the config directory; from there open the urls.py file for editing. Add your polls urls to the ```urlpatterns``` list (which is located on line 8) so that it looks like the following:
```
urlpatterns = [
    path("", TemplateView.as_view(template_name="pages/home.html"), name="home"),
    path(
        "about/", TemplateView.as_view(template_name="pages/about.html"), name="about"
    ),
    # Django Admin, use {% url 'admin:index' %}
    path(settings.ADMIN_URL, admin.site.urls),
    # User management
    path("users/", include("mysite_cookiecutter.users.urls", namespace="users")),
    path("accounts/", include("allauth.urls")),
    # Your stuff: custom urls includes go here
    path("polls/", include("polls.urls"))
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```
Save the changes. Note the "Your stuff: custom urls includes go here" comment on line 18. Below that line is your custom urls for your polls app.  
Now within the config directory, open the settings directory and open the local.py file for editing. On line 14 in the ```ALLOWED_HOSTS``` list add "192.168.99.100" to the list so that it looks like:
```
ALLOWED_HOSTS = ["localhost", "0.0.0.0", "127.0.0.1", "192.168.99.100"]
```
Save the changes. Now go back to your git bash and change to the "mysite_cookiecutter" directory. To build your stack run the following command: 
```
$ docker-compose -f local.yml build
```
This will take a while to complete. Once your stack is built, run the following command to create a superuser for your admin console:
```
$ docker-compose -f local.yml run --rm django python manage.py createsuperuser
```
Now run the stack with the following command:
```
$ docker-compose -f local.yml up
```
