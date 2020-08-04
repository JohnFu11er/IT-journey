---
layout: post
title: "Working with variables in Ansible"
date: 2020-08-05 08:00:00 -0400
categories: jekyll update
---
Variables can be defined several ways in Ansible. The below examples are running on the localhost (computer your are running ansible on).

<b>Assign variables in a playbook</b>
{% highlight ansible %}
---
# Filename: Variable_test.yml
  - name: Variable Example Playbook
    hosts: all
    connection: network_

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