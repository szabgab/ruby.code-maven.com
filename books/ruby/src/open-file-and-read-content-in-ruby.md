# Open file and read content in Ruby


Reading the content of a file is one of the most important tasks in any programming language. In Ruby it is very easy to do so.


```ruby
{{#include examples/ruby/read_file.rb }}
```

```
ruby read_file.rb  some/file.txt
```

This program expects us to supply the name of a file on the the command line and then uses [ARGV](/argv-the-command-line-arguments-in-ruby)
to access this value. Actually at first we check if the user has supplied the correct number of parameters and
exit the program if not.

Then we use the `open` call top open the file for reading. This will return an
instnce of the the [File](http://ruby-doc.org/core/File.html) class.

(If we printed out the content of `fh` we would get something like `#&lt;File:0x007f8c0310f748&gt;`

The `read` method of this class will read in the content of the file and we have assigned it to the varibale
`content`. This is the whole content of the file, including the embedded newlines.

This is basicallt the same as the [slurp mode in Perl](https://perlmaven.com/slurp)


## Read file line-by-line

Reading in the whole file in one operation as seen above is easy, but not necessarily a good idea.
For example if you have a 10 Gb log file, you probably would not want to read the whole thing into memory.
Do you even have 10 Gb free memory?

In such cases it is probably better to read the file line-by-line. After reading each line,
do whatever processing you need to do on that line and then, replace it with the next line.
This way at any given time we only hold one line in memory. Much more efficient.

There are actually at least two ways to write this and I am not sure if there is any advantage/disadvantage
in either of them.

This first one using `gets` and `while` looks more similar to what someone coming form Perl 5 would write:

```ruby
{{#include examples/ruby/read_file_by_line_while.rb }}
```

The other one using `each` looks more Rubyish:

```ruby
{{#include examples/ruby/read_file_by_line_each.rb }}
```

timestamp: 2015-10-11T12:30:01
tags:
  - open
  - File
  - read
  - readline
  - gets
  - while
  - each

