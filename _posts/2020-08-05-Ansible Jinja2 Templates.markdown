---
layout: post
title: "Working with Jinja2 Templates in Ansible"
date: 2020-08-05 09:00:00 -0400
categories: jekyll update
---
<b><text style="color: red"> - </text></b>Jinja2 is a modern and designer-friendly templating language for Python that is used by Ansible to enable dynamic expressions and access to variables.<br>
<b><text style="color: red"> - </text></b>With Jinja2 templates, Ansible users are able to populate a template before the task is sent and executed on the target machine.<br>

<h1><b><u>View the content of the ansible_facts variable from the local host</u></b></h1>
<b><text style="color: red"> Step 1 </text></b>Create a new directory named: jinja_lab_1<br>
<b><text style="color: red"> Step 2 </text></b> Navigate to the new directory jinja_lab_1 and create a file named: jinja_lab_1.yml (see below):<br>
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

<b><text style="color: red"> Step 3</text></b> Run the playbook by entering the following code in the terminal window while in the jinja_lab_1 directory<br>
{% highlight html %}
ansible-playbook jinja_lab_1.yml
{% endhighlight %}

<b><text style="color: red"> Step 4 </text></b> You should now see a long dictionary of green text that are key/value pairs seperated by ":". Each of these values was gathered by ansible when it ran the "jijna_lab_1.yml" playbook. Scroll up through the green text until you get to the top of the section titled "TASK [display the contents of ansible_facts]. You shoud see code similar to the code below. The first key in the dictionary is "ansible_facts" which has a nested dictionary as it's value.  This nested dictionary's first key is "all_ipv4_addresses", whose value is "192.168.x.x" (see below):<br>
{% highlight html %}
TASK [display the contents of ansible_facts]************************
ok: [localhost] => {
    "ansible_facts": {
        "all_ipv4_addresses": [
        "192.168.x.x"
        ]
        ...

{% endhighlight %}

<h1><b><u>Parse ansible_facts to display the value of a dictionary key</u></b></h1>
<b><text style="color: red"> Step 1 </text></b> Create a new directory named: jinja_lab_2<br>
<b><text style="color: red"> Step 2 </text></b> Navigate to the new directory jinja_lab_2 and create a file named: jinja_lab_2.yml (see below):<br>
{% highlight yaml %}
# Filename: jinja_lab_2.yml
---
  - name: jinja lab 2
    hosts: localhost

    tasks:
      - name: parse and display the contents of ansible_facts
        debug:
          var: ansible_facts["all_ipv4_addresses]
{% endhighlight %}

<b><text style="color: red"> Step 3</text></b> Run the playbook by entering the following code in the terminal window while in the jinja_lab_2 directory<br>
{% highlight html %}
ansible-playbook jinja_lab_2.yml
{% endhighlight %}

<b><text style="color: red"> Step 4</text></b> Verify that the IPv4 addresses of your loocalhost are listed. For example:<br>
{% highlight html %}
TASK [display "all_ipv4_addresses"]************************
ok: [localhost] => {
    "ansible_facts[\"all_ipv4_addresses\"]": [
        "192.168.x.x"
    ]
}
{% endhighlight %}

<h1><b><u>Assign parsed ansible_facts to new variable names in a playbook</u></b></h1>
<b><text style="color: red"> Step 1 </text></b> Create a new directory named: jinja_lab_3<br>
<b><text style="color: red"> Step 2 </text></b> Navigate to the new directory jinja_lab_3 and create a file named: jinja_lab_3.yml (see below):<br>
{% highlight yaml %}
# Filename: jinja_lab_3.yml
---
  - name: jinja lab 3
    hosts: localhost

    vars:
      ipv4_adds: "{{ ansible_facts.all_ipv4_addresses.0 }}"
      hostname: "{{ ansible_facts.hostname }}"
      
    tasks:
      - name: parse ansible_facts and assign to new variable
        debug:
          msg: "The first listed ipv4 address of your computer named {{ hostname }} is: {{ ipv4_adds }}"
{% endhighlight %}




