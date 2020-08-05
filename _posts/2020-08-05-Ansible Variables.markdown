---
layout: post
title: "Working with variables in Ansible"
date: 2020-08-05 08:00:00 -0400
categories: jekyll update
---
Variables can be defined several ways in Ansible. The below examples are running on the localhost (computer your are running ansible on).

<h1><b>Ansible Special Variables</b></h1>
These are Ansible's three types of built-in variables:
    
<b>Magic variables - </b> Variables that cannot be set directly by the user. For example:<br>
&emsp; <b><text style="color: red">inventory_hostname</text></b> - The inventory name for the ‘current’ host being iterated over in the play<br>

<b>Facts - </b> Variables that contain information pertinent to the current host (inventory_hostname). They are only available if gathered first. Gathering of facts is the default setting, and may be turned off with: gather_facts= no. For Example: <br>
&emsp; <b><text style="color: red">ansible_facts</text></b> - Contains any facts gathered or cached for the inventory_hostname<br>

<b>Connection variables -  </b> Variables that specify how to execute actions on a target. For Example: <br>
&emsp; <b><text style="color: red">ansible_connection </text></b> - Connection plugin actually used for the task on the target host.<br>
&emsp; <b><text style="color: red">ansible_host </text></b> - The IP/name of the target host to use instead of inventory_hostname.<br>
&emsp; <b><text style="color: red">ansible_user </text></b> - the user Ansible "logs in" as.<br>

<h1><b><u>Assigning variables in a playbook</u></b></h1>
&emsp; <b><text style="color: red"> - </text></b>Variables are created by defining their name and value under the section of your playbook named "vars:"<br>
&emsp; <b><text style="color: red"> - </text></b>Varibles are then called with the name of the variable encapsulated with double curly-braces {{'{{'}} variable_name }}<br>
{% highlight yaml %}
---
# Filename: Variable_test.yml
  - name: Variable Example Playbook
    hosts: localhost

    vars:
      directory_name: notes
      file_name: sprint_review

    tasks:
      - name: Create a directory named "notes" in the current directory
        file:
          path: ./{{'{{'}} file_name }}
          state: directory

      - name: Create a file named "sprint_review" in the "notes" directory ./notes
        file:
          path: ./{{'{{'}} directory_name }}/{{'{{'}} file_name }}
          state: touch
{% endhighlight %}

<h1><b><u>Assigning variables in an inventory file</u></b></h1>
<b><text style="color: red"> - </text></b>Step 1: Make a new directory named: Lab_2<br>
<b><text style="color: red"> - </text></b>Step 2: Create the ansible.cfg file in the Lab_2 directory (see below)<br>

{% highlight yaml %}
# Filename: ansible.cfg
[defaults]
invnetory= inventory
{% endhighlight %}

<b><text style="color: red"> - </text></b>Step 3: Create the inventory file in the Lab_2 directory (see below)<br>
{% highlight yaml %}
# Filename: inventory
[all:hosts]
localhost

[all:vars]
ansible_connection= local
directory_name= notes
file_name= sprint_review
{% endhighlight %}

<b><text style="color: red"> - </text></b>Step 4: Create the Lab_2.yml file in the Lab_2 directory (see below)

{% highlight yaml %}
---
# Filename: Lab_2.yml
  - name: Variable Example Playbook
    hosts: all

    tasks:
      - name: Create a directory named "notes" in the current directory
        file:
          path: ./{{'{{'}} directory_name }}
          state: directory

      - name: Create a file named "sprint_review" in the "notes" directory ./notes
        file:
          path: ./{{'{{'}} directory_name }}/{{'{{'}} file_name }}
          state: touch

{% endhighlight %}

<h1><b><u>Assigning host variables in an inventory file</u></b></h1>
{% highlight ansible %}

{% endhighlight %}