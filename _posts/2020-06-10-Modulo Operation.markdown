---
layout: post
title: "Modulo Operation Example in Python"
date: 2020-06-10 07:15:00 -0400
categories: jekyll update
---
Below is an example of using the [modulo operation][modulo-operation] to solve a problem related to factors of a number:


Your task is to convert a number into a string that contains raindrop sounds corresponding to certain potential factors.
A factor is a number that evenly divides into another number, leaving no remainder. The simplest way to test if a one
number is a factor of another is to use the modulo operation.

{% highlight python %}
The rules of raindrops are that if a given number:

has 3 as a factor, add 'Pling' to the result.
has 5 as a factor, add 'Plang' to the result.
has 7 as a factor, add 'Plong' to the result.
does not have any of 3, 5, or 7 as a factor,
    the result should be the digits of the number.
{% endhighlight %}

Possible solution:
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

[modulo-operation]: https://en.wikipedia.org/wiki/Modulo_operation