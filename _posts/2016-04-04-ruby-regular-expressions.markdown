---
title: "Ruby: Regular Expressions and MatchData Basics"
subtitle: "An Essential Tool for the Rubyist"
date: 2016-04-04
categories: ruby
---

I've used regular expressions before in SQL and Google Analytics, but there's something intimidating about the way they look in Ruby sometimes that has stopped me from delving into them so far. For instance => `(s =~ /<0(x|X)(\d|[a-f]|[A-F])+>/)`. What kind of insanity is that? It honestly looks like someone just mashed the keyboard. Yet, I know how helpful understanding regular expressions can be, so I decided I had to do some research and get to know them better.

Let's start off with some basics. A regular expression is used for pattern matching. With them you can test a string to see if it contains a pattern, you can extract characters from a string, and you can change a string.

Take this string, for example:

{% highlight ruby %}
string = "Ahh, a bear in his natural habitat...a Studebaker."
{% endhighlight %}

To check if the word "Studebaker" is in the string, we could do it like this:

{% highlight ruby %}
string =~ /Studebaker/ #=> 39
{% endhighlight %}

Wait. Why does it return "39?" The =~ operator returns the number that the match starts on. If we want, we can create a MatchData object by calling the match method and storing the results to a variable.

{% highlight ruby %}
match_studebaker = /Studebaker/.match(string) #=> <MatchData "Studebaker">
{% endhighlight %}

Now we can call to_s on match_studebaker.

{% highlight ruby %}
match_studebaker.to_s #=> "Studebaker"
{% endhighlight %}

Since we might not know if the word is capitalized or not we could try something like this:

{% highlight ruby %}
match = /studebaker/.match(string.downcase) #=> <MatchData "studebaker">
{% endhighlight %}

And it works. However, the string in the MatchData object now has a lowercase "s." We could alter our regular expression a bit to accomplish the same thing.

{% highlight ruby %}
match = /[sS]tudebaker/.match(string) #=> <MatchData "Studebaker">
{% endhighlight %}

With this method we have the added benefit of not altering the original case of the matched pattern as well. There are a number of other useful methods in the MatchData class. If you'd like to learn more, you can [view them here][ruby-docs].

[ruby-docs]: http://ruby-doc.org/core-1.9.3/MatchData.html
