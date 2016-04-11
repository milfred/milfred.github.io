---
title: "The Differences Between Arrays and Hashes in Ruby"
date: 2016-03-06
categories: ruby
---

In Ruby, an array and a hash are similar in the sense that they are both containers for a group of objects that act like variables. In an array, each object in the array is indexed with an integer starting with zero. A hash, on the other hand, uses a key/value pair to access the index. The key can be any type of object (string, integer, etc.).

Arrays
------

Values in an array are comma separated and wrapped in brackets.

{% highlight ruby %}
spinal_tap = ["David St. Hubbins", "Nigel Tufnel", "Derek Smalls"]
{% endhighlight %}

So "David St. Hubbins" could be accessed by calling:

{% highlight ruby %}
spinal_tap[0] #=> "David St. Hubbins"
{% endhighlight %}

Hashes
------

Key/value pairs in a hash can be separated with two different syntaxes. `=>` (referred to as 'hash rocket'), or `:`. If you use a colon, the key will be a `symbol`. For more information about symbols and how they differ from strings, [look here][ruby-docs-symbol].

{% highlight ruby %}
spinal_tap = {
  david: {
    name: "David St. Hubbins",
    role: ["lead singer", "rhythm guitar"] },
  nigel: {
    name: "Nigel Tufnel",
    role: "lead_guitar" },
  derek: {
    name: "Derek Smalls",
    role: "bass" }
}
{% endhighlight %}

Values can be accessed by calling the key assigned to it. The example above is a multi-dimensional hash or, as I once heard it referred to, a "hashy hash." Here, "David St. Hubbins" can be accessed by calling:

{% highlight ruby %}
spinal_tap[:david][:name] #=> "David St. Hubbins"
{% endhighlight %}

If we want to see what David's role is in the band we can say:

{% highlight ruby %}
puts spinal_tap[:david][:role] #=>
# lead singer
# rhythm guitar
{% endhighlight %}

[ruby-docs-symbol]: http://ruby-doc.org/core-2.3.0/Symbol.html