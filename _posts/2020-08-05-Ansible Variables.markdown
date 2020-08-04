---
layout: post
title: "Working with variables in Ansible"
date: 2020-08-05 08:00:00 -0400
categories: jekyll update
---
Variables can be defined several ways in Ansible:

1. Assign variables in a playbook
{% highlight ansible %}
---
# File: Variable_test.yml
  - name: Variable Example Playbook
    hosts: localhost
    gather_facts: yes

    vars:
      user_name: Bill
      group_name: Bill

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