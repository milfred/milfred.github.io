---
title:  "Ruby: Using Instance Variables"
date:   2016-03-21
categories: ruby
---

It can sometimes be confusing to know when to use an instance method or variable. Below I've created an example of a class that models a guitar and strumming each string. It takes two arguments. The first argument is the number of the string (starting from the top) you want to strum. The second is how many total strings you want to strum. The output would will be the notes that the guitar would play given the arguments.

We'll figure out when we need to use instance methods and variables in this example. Look it over and try to figure out if all of the methods really need to be instance methods.

{% highlight ruby %}
class Guitar
  def initialize(string_num, num_of_strings)
    @string_num = string_num
    @num_of_strings = num_of_strings
    @notes = ["E", "B", "G", "D", "A", "E"]
  end
  def strum
    if 6 - (@string_num - 1) < @num_of_strings
      puts "This is a basic 6-string. You may have a fancy 12-string at home, but that\'s too many strings for this guitar."
    else
      puts @notes.slice(@string_num - 1, @num_of_strings).join(", ")
    end
  end
end
{% endhighlight %}

What do you think? The answer is yes. They all need to be instance methods because we need to share the data that is stored in them with other methods.

Now let's add another feature to our guitar. A method to retune it. Take a look and see if it looks correct.

{% highlight ruby %}
class Guitar
  def initialize(string_num, num_of_strings)
    @string_num = string_num
    @num_of_strings = num_of_strings
    @notes = ["E", "B", "G", "D", "A", "E"]
  end
  def strum
    if 6 - (@string_num - 1) < @num_of_strings
      puts "This is a basic 6-string. You may have a fancy 12-string at home, but that\'s too many strings for this guitar."
    else
      puts @notes.slice(@string_num - 1, @num_of_strings).join(", ")
    end
  end
  def new_tuning(new_notes)
    @new_tune = new_notes.reverse
    @notes = @new_tune
    puts "You have tuned the guitar to #{new_notes.join(", ")}."
  end
end
{% endhighlight %}

This code will run perfectly, but there is one variable that doesn't need to be an instance variable. The "@new_tune" variable isn't being used outside of the new_tuning method, so it doesn't need to be an instance method. We could just leave it, but let's say we keep expanding our Guitar class and adding new methods. Maybe I add a feature to create a new song some day and I decide to create an instance variable called "@new_tune." That could cause some bugs in my program.This code will run perfectly, but there is one variable that doesn't need to be an instance variable. The "@new_tune" variabe isn't being used outside of the new_tuning method, so it doesn't need to be an instance method. We could just leave it, but let's say we keep expanding our Guitar class and adding new methods. Maybe I add a feature to create a new song some day and I decide to create an instance variable called "@new_tune." That could cause some bugs in my program.

Here is what the new method should look like to prevent issues like that.

{% highlight ruby %}
  def new_tuning(new_notes)
    new_tune = new_notes.reverse
    @notes = new_tune
    puts "You have tuned the guitar to #{new_notes.join(", ")}."
  end
  {% endhighlight %}