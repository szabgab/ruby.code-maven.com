# Hello World using CGI in Ruby


The [Hello World exercise](/exercise-web-hello-world) is usually the first thing people do in every language and
in every environment. Here we are going to do it using Ruby and the cgi module that comes with Ruby.


## Hello World in plain Ruby

Writing a Hello World! script in Ruby that can run as a CGI program is quite simple.
You need to make sure that your web [server is set up to handle CGI requests](/set-up-cgi-with-apache),
and then you need to create a simple script:

```ruby
{{#include examples/ruby/web_hello_world.rb }}
```

It has a few elements that other, command line script, might not necessarily need.

The first line, also called the [hashbang](https://perlmaven.com/hashbang) line needs to point to the Ruby interpreter/compiler.
in our case this means the first line is `#!/usr/bin/ruby`. Please note, there are no spaces in that line and it must be the first
line in the file. It is used by Apache and the Unix/Linux environment to determine which interpreter will understand the code in this file.

Then, before we print out any of the real HTML content, we need to send out the HTML header followed by an empty row.
At least we need to print out the Content-type. Therefore the next line is printing the `content-type` followed
by two newlines. The first is the end of the Content-type line, the second is the end of the empty row.

Then can come the actual content of the page. In our case this is a simple string that reads `Hello World!`


We need to place the file in a directory that was configured to handle CGI script and we need to make the file executable by running

```
$ sudo chmod +x web_hello_world.rb
```

Once we have this we can use our regular browser, or `curl` to access the appropriate URL.


## Hello World in Ruby using the cgi module

While in this simple case we could get by without any module, I think it is important to see how the "Hello World" script
can be written using the [cgi](http://ruby-doc.org/stdlib-2.1.2/libdoc/cgi/rdoc/CGI.html) module that comes with ruby.

```ruby
{{#include examples/ruby/web_hello_world_cgi.rb }}
```

The difference is that in this case we use the `header` method of the `cgi` instance to create the `Content-type`
line. There is nothing special here, except maybe that you don't need to remember the content type of an HTML page.

timestamp: 2015-11-12T14:00:01
tags:
  - cgi

