---
layout: post
title: "Modulo Operation Example"
date: 2020-06-10 07:15:00 -0400
categories: jekyll update
---

{% highlight python %}

def raindrops(number):
    output = []
    if number % 3 == 0:
        output.append("Pling")
    if number % 5 == 0:
        output.append("Plang")
    if number % 7 == 0:
        output.append("Plong")
    if output == []:
        output.append(number)
    return output

while True:
    user_input = int(input("Enter a number: "))
    print(raindrops(user_input))

{% endhighlight %}
