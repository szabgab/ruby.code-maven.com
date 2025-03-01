# split in Ruby


[String](http://ruby-doc.org/core-2.2.0/String.html) objects in Ruby have a method called
[split](http://ruby-doc.org/core-2.2.0/String.html#method-i-split). It is similar to the
[split function of Perl](https://perlmaven.com/perl-split). It can cut up a string into
pieces along a pre-defined string or regex returning an array of smaller strings.


In the first example you can see how to split a string every place where there is a comma `,`:

```ruby
{{#include examples/ruby/split_comma.rb }}
```


In the second example we use a Regex to match the places where we would like to cut up the string.
It makes the splitting much more flexible:

```ruby
{{#include examples/ruby/split_regex.rb }}
```


## Split with limit

We can pass a second parameter to `split` that will limit the number of reurned valus.
If we pass 3, then split will make two cuts and return the results:

```ruby
{{#include examples/ruby/split_comma_limit.rb }}
```

## Split by empty string

As a slightly special case, if we use an empty string (or empty regex) to split with,
then we will get back an array of the individual characters:

```ruby
{{#include examples/ruby/split_by_empty_string.rb }}
```


timestamp: 2015-10-31T12:00:01
