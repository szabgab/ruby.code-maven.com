# Getting started with Ruby

I have started to learn Ruby at [Try Ruby](http://tryruby.org/) Here is what I've learned so far.


```
$ ruby --version
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
```

## print and puts

The first thing we should try is printing to the screen.
I've created a file with `.rb` extension. Not that it matters a lot,
but I think editors and IDEs will recognize that this is a Ruby file by that extension
and will be able to put nice colors on the various parts of the code.

```ruby
{{#include examples/ruby/hello_world.rb }}
```

I ran the code and got:

```
$ ruby examples/ruby/hello_world.rb

Hello World
Hi
examples/ruby/hello_world.rb:5:in `<main>': uninitialized constant Foo (NameError)
```

So calling `print` will print to the screen exactly what I gave to it.
Calling `puts` will do the same, but it will also add a newline at the end of the output.
If I want `print` to add a newline I can include `\n` in my string.

The last output is an error. It shows that we <b>have to</b> put the strings in quotes.

## Comments

We can `#` after a statement or even as the first character of a line and everything to the
right of this character (including this character) will be disregarded by Ruby.
Very handy to add comments for the next person looking at the code.

## Arithmetic

Part of programming is calculating stuff by using various arithmetic operations.
Let's see how does that work in Ruby:

```ruby
{{#include examples/ruby/arithmetic.rb }}
```

(The output of each line was added as a comment on the same line.)

The basic operation such as `+`, `-`, `*` work as they should.

`**` is the exponent operation so `2**3 = 2*2*2 = 8`

At first it seems that division also works as expected, `8/2 = 4` but then it turns out that
`3/2 = 1`.

Apparently if both numbers in a division are whole numbers, then Ruby will also return a whole number.

On the other hand, if either (or both) the numbers are floating point numbers (they have a decimal point in them)
then the result will be also floating point. Even if the value after the decimal point is 0 (`4/2.0 = 2.0`).

Dividing by 0 generates an exception called `ZeroDivisionError` and stops the program.
(We did not reach the `puts 'done'` statement.

## Ruby strings

We saw arithmetic operations on numbers, but we can also use some operations on strings:

```ruby
{{#include examples/ruby/strings.rb }}
```

Becasue in Ruby everything is an object, there are certain methods we can run on a string.
For example the `length` method will return the number of characters in the string.

The `reverse` method will return the characters in reverses order.

We can use the `*` multiplicator on a string. It will return (and `puts` will display)
a new string in which we have several (in this case 2) copies of the original string.

If we want to have 3 copies of the number 2, we have a number of options.

`puts 2 * 3              # 6`

this one is not doint that, as the `*` between two numbers will multiply them.

We can put the number 2 in quotes:

`puts "2".to_s * 3       # 222`

or we can use the `to_s` to conver the number to a string. 

`puts 2.to_s * 3         # 222`

This will be much more interesting once we start to use variables.

Finally, if we new that we want 3 copies of the number 2, we could have just written "222"
without trying to use all kinds of Ruby operations.


Absolutely finally, let's see what happens if we swap the string and the number in this multiplication
operation:

`puts 2 * "Jar "`

We get an excpetion:

```
    examples/ruby/strings.rb:7:in `*': String can't be coerced into Fixnum (TypeError)
       from examples/ruby/strings.rb:7:in `<main>'
```

I guess we cannot do that.

timestamp: 2015-02-08T15:30:01
tags:
  - print
  - puts
  - length
  - reverse
  - to_s

