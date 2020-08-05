---
layout: post
title: "Working with Jinja2 Templates in Ansible"
date: 2020-08-05 09:00:00 -0400
categories: jekyll update
---
Jinja2 is a modern and designer-friendly templating language for Python that is used by Ansible to enable dynamic expressions and access to variables.  With Jinja2 templates, Ansible users are able to populate a template before the task is sent and executed on the target machine.<br>

<h1><b><u>View the content of the ansible_facts variable from the local host</u></b></h1>
Step 1 Create a new directory named: jinja_lab_1
Step 2 Navigate to the new directory jinja_lab_1 and create a file named: jinja_lab_1.yml (see below):<br>
{% highlight yaml %}
# Filename: jinja_lab_1.yml
---
  - name: jinja lab 1
    hosts: localhost

    tasks:
      - name: display the contents of ansible_facts
        debug:
         var: ansible_facts
{% endhighlight%}
Step 3 Verify that the contents of the ansible_facts varible are displayed on the screen.  You will see green text that is formatted as a dictionary with ":" seperated key/value pairs.<br>

<h1><b><u>Parse the contents of the ansible_facts variable to display specific value of a designated dictionary key.</u></b></h1>

