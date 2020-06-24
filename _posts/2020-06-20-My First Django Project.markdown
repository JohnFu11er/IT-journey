---
layout: post
title: "My first Django project"
date: 2020-06-20 12:23:00 -0400
categories: jekyll update
---
Having never used Django before, but hearing about it from several people, I decided to look at this powerful program.

Below is an example of a simple Hello World webpage built with Django.  This guide was built following [this video][django-howto].
<br/>
<br/>
<br/>

<h2>DJANGO SETUP</h2>

<b>Provision a CentOS 8 virtual machine.  Make sure that your system user is in the administrator group, and that the VM has internet connectivity. Once CentOS 8 is done installing, open a terminal window from the desktop.</b><br />
<br />

<b>Add EPEL repository:</b>
{% highlight python %}
[user@local ~]$ sudo yum install epel-release
{% endhighlight %}<br />

<b>Install all applicable updates (this may take several minutes):</b>
{% highlight python %}
[user@local ~]$ sudo yum update
{% endhighlight %}<br />

<b>Install Python3.6 or better:</b>
{% highlight python %}
[user@local ~]$ sudo yum install python36
{% endhighlight %}<br />

<b>Import Microsoft GPG key:</b>
{% highlight python %}
[user@local ~]$ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
{% endhighlight %}<br />

<b>Create a new repository file for the Visual Studio Code (VS Code) repository:</b>
{% highlight python %}
[user@local ~]$ sudo vi /etc/yum.repos.d/vscode.repo
{% endhighlight %}<br />

<b>Configure the repository file to point to the VS Code repository by pressing “i” and then entering the following:</b>
{% highlight python %}
[code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc
{% endhighlight %}<br />

<b>Save and close the vscode.repo file:</b>
{% highlight python %}
ctrl + c
:wq
{% endhighlight %}<br />

<b>Install VS Code:</b>
{% highlight python %}
[user@local ~]$ sudo yum install code
{% endhighlight %}<br />

<b>Create project directory in user home folder:</b>
{% highlight python %}
[user@local ~]$ mkdir my_django_project
{% endhighlight %}<br />

<b>Navigate to your project directory:</b>
{% highlight python %}
[user@local ~]$ cd my_django_project
{% endhighlight %}<br />

<b>Create a python virtual environment:</b>
{% highlight python %}
[user@local my_django_project]$ python3 -m venv django-env
{% endhighlight %}<br />

<b>active the newly create environment:</b>
{% highlight python %}
[user@local my_django_project]$ . django-env/bin/activate
{% endhighlight %}<br />

<b>Your prompt should now be:</b>
{% highlight python %}
(django-env) [user@local my_django_project]$
{% endhighlight %}<br />

<b>Install Django:</b>
{% highlight python %}
(django-env) [user@local my_django_project]$ pip install django
{% endhighlight %}<br />
<br />

<h2>Django project setup</h2>

<b>Create your Django project titled “first_project”:</b>
{% highlight python %}
(django-env) [user@local my_django_project]$ django-admin startproject first_project
{% endhighlight %}<br />

<b>Change to your first_project directory:</b>
{% highlight python %}
(django-env) [user@local my_django_project]$ cd first_project/
{% endhighlight %}<br />

<b>Start the Django development web server:</b>
{% highlight python %}
(django-env) [user@local my_django_project/first_project]$ python manage.py runserver
{% endhighlight %}<br />

<b>Open your web browser and type the following in the navigation line:</b>
{% highlight python %}
http://127.0.0.1:8000
{% endhighlight %}

You should see a Django welcome page that tells you your install was successful. If you do not see this, go back, and review the steps above.
<br />
<br />
<br />


<h2>Build your first webpage</h2>

<b>Open VS Code from your project’s folder:</b>
{% highlight python %}
(django-env) [user@local my_django_project/first_project]$ code .
{% endhighlight %}<br />

<b>Create a new file for your webpage:</b>
<p style="margin-left: 40px">Right click on >first_project</p>
<p style="margin-left: 40px">Click new file</p>
<p style="margin-left: 40px">Name the file views.py</p>
<br/>

<b>Click on the view.py file to access it, add the following lines of code, and save the view.py file:</b>
{% highlight python %}
from django.http import HttpResponse

def welcome (request):
    return HttpResponse(“Hello, World!”)
{% endhighlight %}<br /> 

<b>Add a URL path to the project for your new webpage by opening the urls.py file, adding the lines of code below, and saving the file (VS Code should auto-save the file, but you can check by clicking on “File”, then seeing if there is a check mark to the left of “Auto Save”).</b>
{% highlight python %}
from django.urls import path
from .views import welcome

urlpatterns = [
path(‘admin/’, admin.site.urls),
path(‘welcome’, welcome)
]
{% endhighlight %}<br />

<b>View your new webpage by opening your web browser and navigating to the following address:</b>
{% highlight python %}
http://127.0.0.1:8000/welcome
{% endhighlight %}



[django-howto]:https://www.youtube.com/watch?v=ovql0Ui3n_I&t=598s