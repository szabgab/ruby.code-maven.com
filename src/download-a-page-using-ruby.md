# Download an HTML page using Ruby


While a page on a web-site is totally different from a file, several languages provide a way to read them as if they were regular files.
I am not sure if this is a good idea, but it certainly works for some people.

In Ruby, the [open-uri](http://ruby-doc.org/stdlib-2.1.0/libdoc/open-uri/rdoc/OpenURI.html) modules provides this simplified interface.


After loading the module with `require` it overrides the standard `open` function so from now on,
in addition to [opening regular files](/open-file-and-read-content-in-ruby),
it will be able to 'open' URLs as well. Of course, it can only open them read-only as
we can only fetch pages cannot push them out, but it can get all kinds of additional parameters.

```ruby
{{#include examples/ruby/download.rb }}
```

The `open` in such cases will return an instance of `StringIO`.
If we were printing out the contet of `fh` we would get:

```
puts fh   #  #&lt;StringIO:0x007fc41c8bc238&gt;
```

Once we get the object we can apply the same methods as on a regular filehandle. For example we can use the `read` method
to read in the content of the whole page.  As opposed to the case when we [read regular files,](/open-file-and-read-content-in-ruby),
in this case there is no efficiency reason to read the content line-by-line. The way HTTP works it does not make much sense. By the time
we start reading the page the whole document have arrived and is located in the memory of our program. We can as well copy it
to our internal variable using the `read` method.


## Lie about who are we

When a browser accesses a web site it tells the site what kind of browser is that, which version etc.
The same happens when we "open" a web page using the `open` function supplied by the `open-uri` module.

By default, `opern-uri` calls it 'browser' `Ruby` which does not say much.
We can change it to whatever we want by passing "User-Agent" to the `open` call:

```ruby
{{#include examples/ruby/download_user_agent.rb }}
```

This string will be written in the Access log of the web server we connect to.

timestamp: 2015-10-11T16:30:01
tags:
  - open-uri
  - User-Agent

