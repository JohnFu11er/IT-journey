---
layout: post
title: "My first Django project"
date: 2020-06-20 12:23:00 -0400
categories: jekyll update
---
Having never used Django before, but hearing about it from several people, I decided to look at this powerful program.

Below is an example of a simple Hello World webpage built with Django.  This is by no means the extent of Django's capabilities.

Django steps:
1.	Prepare the environment
    a.	Provision CentOS 8 virtual machine. Once CentOS 8 is done installing, open a terminal window from the desktop
    b.	Add EPEL repository
        [user@local ~]$ sudo yum install epel-release
    c.	Install all applicable updates (this may take several minutes)
        [user@local ~]$ sudo yum update
    d.	Install Python3.3 or better
        [user@local ~]$ sudo yum install python36
    e.	Import Microsoft GPG key
        [user@local ~]$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    f.	Create a new repository file for the Visual Studio Code (VS Code) repository
        [user@local ~]$ sudo etc/yum.repos.d/vscode.repo
    g.	Open the repository file created in the previous step
        [user@local ~]$ sudo vi /etc/yum.repos.d/vscode.repo
    h.	Configure the repository file to point to the VS Code repository by pressing “i” and then entering the following:
        [code]
        name=Visual Studio Code
        baseurl=https://packages.microsoft.com/yumrepos/vscode
        enabled=1
        gpgcheck=1
        gpgkey=https://packages.microsoft.com/keys/microsoft.asc
    i.	Save and close the vscode.repo file:
        ctrl + c
        :wq
    j.	Install VS Code
        [user@local ~]$ sudo yum install code
    k.	create project directory in user home folder
        [user@local ~]$ mkdir my_django_project
    l.	Navigate to your project directory
        [user@local ~]$ cd my_django_project
    m.	Create a python virtual environment
        [user@local my_django_project]$ python3 -m venv django-env
    n.	active the newly create environment
        [user@local my_django_project]$ . django-env/bin/activate
    o.	Your prompt should now be:
        (django-env) [user@local my_django_project]$
    p.	Install Django:
        (django-env) [user@local my_django_project]$ pip install django

2.	Django project setup
a.	Create your Django project titled “first_project”:
(django-env) [user@local my_django_project]$ django-admin startproject first_project
b.	Change to your first_project directory:
(django-env) [user@local my_django_project]$ cd first_project/
c.	Start the Django development web server:
(django-env) [user@local my_django_project/first_project]$ python manage.py runserver
d.	Open your web browser and type the following in the navigation line:
http://127.0.0.1:8000
You should see a Django welcome page that tells you your install was successful.
If you do not see this, go back, and review the steps above
3.	Build your first webpage
a.	Open VS Code from your project’s folder
(django-env) [user@local my_django_project/first_project]$ code .
b.	Create a new file for your webpage
Right click on >first_project
Click new file
		Name the file views.py
c.	Click on the view.py file to access it, add the following lines of code, and save the view.py file
from django.http import HttpResponse

def welcome (request):
    return HttpResponse(“Hello, World!”)
 

d.	Add a URL path to the project for your new webpage by opening the urls.py file, adding the following lines of red code, and saving the file (VS Code should auto-save the file, but you can check by clicking on “File”, then seeing if there is a check mark to the left of “Auto Save”)
…
from django.urls import path
from .views import welcome

urlpatterns = [
    path(‘admin/’, admin.site.urls),
    path(‘welcome’, welcome)
]

e.	View your new webpage by opening your web browser and navigating to the following address
http://127.0.0.1:8000/welcome
