---
layout: post
title: "Working with variables in Ansible"
date: 2020-08-05 08:00:00 -0400
categories: jekyll update
---
Variables can be defined several ways in Ansible. The below examples are running on the localhost (computer your are running ansible on).

<b> Ansible three types of built-in variables </b>
    <b>Magic variables</b> - cannot be set directly by the user. Ex:
        inventory_hostname - The inventory name for the ‘current’ host being iterated over in the play
    
    <b>Facts</b> - variables that contain information pertinent to the current host (inventory_hostname). They are only available if gathered first. Gathering of facts is the default setting, and may be turned off with: gather_facts= no.
        ansible_facts - contains any facts gathered or cached for the inventory_hostname

<b>Assign variables in a playbook</b>
{% highlight ansible %}
---
# Filename: Variable_test.yml
  - name: Variable Example Playbook
    hosts: localhost

    vars:
      file_name: 

    tasks:
      - name: 

{% endhighlight %}

2. Assigning group variables in an inventory file:

{% highlight ansible %}
[routers:vars]
device_type= router

{% endhighlight %}

3. Assigning Host variables in an inventory file:
{% highlight ansible %}

{% endhighlight %}