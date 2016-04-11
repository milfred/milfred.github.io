---
title:  JavaScript Objects Compared to Hashes in Ruby
date:   2016-03-29
categories: ruby javascript
---
My programming education started with Ruby and then jumped over to JavaScript a couple of weeks later. Initially it was very frustrating to make the switch. How many times will I forget to type "var" or a semi-colon before it becomes automatic? At least some things are the same. JavaScript has arrays, so no problem there. But what about hashes? Why does it seem like everything in JavaScript is either a variable or a function anyway? It's kind of confusing. Well, I can help address the hash question at least.

So the good thing about learning more than one programming language is that it forces you to start thinking in terms of concepts and logic, rather than specific language syntax. While JavaScript doesn't have something called a hash like Ruby, they both have associative arrays. That is, a way to store data in key/value pairs.

In Ruby, you create a hash like this:

{% highlight ruby %}
assoc_array = { key: "value" }
{% endhighlight %}

Pretty simple. You give it a name and set it equal to the values inside the curly braces. A key can be any object type (including a hash), but for the most part you'll use a symbol, an integer, a variable, or a string. In the example above, I've used a symbol. In this case you use a colon to separate the key and the array. If you use a different object type as your key you'll need to use the "hash rocket" as a separator. It looks like this: "=>"

To create an associative array in JavaScript your code will look something like this:

{% highlight javascript %}
var assocArray = { key: "value" };
{% endhighlight %}

Not all that different is it? In JavaScript, this data structure is called an "Object" and instead of a key, it's called a "property."

While they look almost exatly the same, there are some differences. The key I used in the Ruby example is a symbol. I'm not going to get too deep into symbols right now, but you use them for a value that won't change in your program. In fact, you technically can't change them. The key I used in the JavaScript example looks the same, but is in fact a string. JavaScript does have a symbol data type now, but using them as properties isn't typically done. This mostly comes into play when you try to call the value of a property in JavaScript.

If you call the value of a pair that uses a symbol for the key in Ruby, it looks like this:

{% highlight ruby %}
hash_name[:key]
{% endhighlight %}

In JavaScript it would look like this:

{% highlight javascript %}
objectName["key"];
{% endhighlight %}