---
layout: post
title: "First experience with Chef"
description: ""
category: ""
tags: ["chef"]
---
{% include JB/setup %}

I'll be honest, many aspects of development seem rather redundant. I'm considering building a layer of abstraction onto various aspects of Chef to make it more useful.

For example, to install a new cookbook (say, apache) you have to type:

{% highlight bash %}
  root@local:# knife cookbook site download apache2
  root@local:# tar zxf apache2-1.8.4.tar.gz
  root@local:# rm apache2-1.8.4.tar.gz
{% endhighlight %}

This is every single time you'd like to add a cookbook... Then you have to add "include\_recipe 'apache2'" to the default.rb in the recipes folder of your cookbook, then you have to add it to your cookbook's metadata.rb as a dependency! ugh.
So let's make it automatic with a simple ruby script (let's call it "getCookbook.rb"). We can even make it a little flexible so if you want to include your personal cookbook, it will add the necessary dependencies.

{% highlight ruby %}
  if ARGV.length >= 1 then
    v1 = ARGV[0]
  end
  
  if ARGV.length == 2 then
    v2 = ARGV[1]
    exists = system("cd " + v2 + " && cd")
    if not exists then
      puts "The cookbook \" + v2 + "\" you want to add \"" + v1 + "\" to doesn't exist!"
      exit
    end
  else
    puts "Usage: ruby getCookbook.rb community_cookbook [your_cookbook]"
  end
  
  success = system( "knife cookbook site download " + v1)
  if success then
    success = system( "tar zxf " + v1 + "*")
    success = system( "rm " + v1 + "*.tar.gz")
    
    if ARGV.length == 2 then
      cookbook = "'" + v1 + "'"
      path = "cookbooks/" + v2
      success = system("echo \"depends " + cb + "\" >> " + path + "/metadata.rb")
      success = system("echo \"include_recipe " + cb + "\" >> " + path + "/recipes/default.rb")
    end
  puts "Successfully installed the \"" + v1 + "\" cookbook!"
  else
  puts "The cookbook \"" + v1 + "\" does not exist!"
  end
{% endhighlight %}

Now you can just call it, and supply a cookbook name. It will either complain if it doesn't exist or successfully download, extract the tarball, clean up and let you know about said success.

{% highlight bash %}
  root@local:# ruby getCookbook.rb apache2
  ...
  ...
  Successfully installed the "apache2" cookbook!
{% endhighlight %}

Obviously this is a simple example, but it doesn't seem to ridiculous to suggest building a library of scripts where you could completely automate the process of setting up and using chef. 
As I continue to explore Chef, I will explore other opportunites like this to make simple scripts to make my life easier.
