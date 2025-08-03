# ARGV - the command line arguments of a Ruby program


When you run a script written in Ruby you can put all kinds of values on the command line after the name of the script:

For example:

`ruby code.rb abc.txt  def.txt qqrq.txt`

or like this:

`ruby code.rb Hello --machine big -d -tl`

The question though, how can the Ruby program know what was given on the command line?


Ruby maintains an array called `ARGV` with the values passed on the command line.
We can access the elements of this array, just as any other array:

`ARGV[0]` is going to be the first value after the name of the script.

We can iterate over the elements either directly with a `for` loop:

```ruby
{{#include examples/ruby/command_line_argv.rb }}
```

or iterating over the [range](/range-in-ruby) of indexes,
and accessing the elements using that index.

```ruby
{{#include examples/ruby/command_line_argv_with_index.rb }}
```

```
$ ruby command_line_argv_with_index.rb foo bar --machine big
0 foo
1 bar
2 --machine
3 big
```


## Verifying the number of arguments

For a simple input validation we can check the length of the `ARGV`
array. Report if we have not received enough arguments and exit the program early.

```ruby
{{#include examples/ruby/command_line_argv_check_length.rb }}
```

Running this script we get:

```
$ ruby command_line_argv_check_length.rb one
Too few arguments

$ ruby command_line_argv_check_length.rb one two
Working on ["one", "two"]
```


## Values received on the command line are strings

In this snippet of code we first check if we got exactly 2 parameters and we do, we add them together:

```ruby
{{#include examples/ruby/command_line_argv_add.rb }}
```

```
ruby command_line_argv_add.rb 23 19
2319
```

The result might not be surprising to you if you know that the values the user passes on the command line are received as strings.
Eeven if they are actually numbers.  If we would like to use them as number we have to convert them using `to_i`:

```ruby
{{#include examples/ruby/command_line_argv_add_numbers.rb }}
```

```
$ ruby command_line_argv_add_numbers.rb 23 19
42
```

timestamp: 2015-10-06T22:30:01
tags:
  - ARGV
  - to_i

