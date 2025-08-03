# Convert String to Number in Ruby


When reading data from a file or from other external resources, they always arrive in Ruby as
[String](http://ruby-doc.org/core-2.2.0/String.html) objects.

If we would like to use them as numbers we first need to convert them to numbers.

But which number and how?


The [String](http://ruby-doc.org/core-2.2.0/String.html) objects in Ruby have several methods to convert
the string object into a number.

* `to_i` will convert the String to an [Integer](http://ruby-doc.org/core-2.2.0/Integer.html).
* `to_f` will convert the String to an [Float](http://ruby-doc.org/core-2.2.0/Float.html), a floating pont
* `to_r` will convert the String to a  [Rational](http://ruby-doc.org/core-2.2.0/Rational.html) number.
* `to_c` will convert the String to a  [Complex](http://ruby-doc.org/core-2.2.0/Complex.html) number.


## Concatenation

Given two numerical values that are actually `String` object (because of the quotation marks around them), if we use the `+`
operator it will work as concatenation.

```
a = "2"
b = "3"
puts a+b  # 23
```


## no implicit conversion of Fixnum into String (TypeError)

If one of the values is a `String` object and the other one is a real number (no quotes), and we try to add them together as
in the next example:

```
puts "2"+3 
```

We'll get an exception: `no implicit conversion of Fixnum into String (TypeError)`


## String tha looks like an integer

A `String` that holds an integer can be converted to an Integer, a Float, a Rational number, or a Complex number:

```
puts a.to_i # 2
puts a.to_f # 2.0
puts a.to_r # 2/1
puts a.to_c # 2+0i
```

## Setting the base: Converting binary, octal, hexadecimal to decimal

Normally `to_i` assumes that our original number in the String object is in 10-base representation, but if you would like to change that?

What if you'd like to treat the String as a binary number, an octal number, or a hexadecimal number? You just pass `base=` with the
appropriate number to the `to_i` method:

```
puts "11".to_i            # 11
puts "11".to_i(base=2)    # 3
puts "11".to_i(base=16)   # 17
```

Of course hexadecimal "numbers" can also contain the letters a-f. The `to_i` fuction can deal with that too.

```
puts "aB".to_i(base=16)   # 171
```

Which brings up the question, what will happen if we use `to_i` without base on a string with hexadecimal number in it,
or just any base with values that are not part of the 'digits' it can handle? They all silently return 0.

```
puts "aB".to_i            # 0
puts "9".to_i(base=8)     # 0
```


That leads us to the question: <b>What happens if not all the characters ar convertable to number?</b>: The answer is simple.
`to_i` will convert all the 'digits' on from the beginning of the string up to the point where it does not understand
any more. Then it will abandon the rest of the string. Even if there are more understandable digits later on.

```
puts "2x3".to_i           # 2
puts "2 3".to_i           # 2
```


## Converting to Floating point and Rational number

We can use the other methods to convert a string to a Floating point, a Rational number, or even a Complex number:
Some of thoes will understand a decimal point in the `String`

```
c = "14.6"
puts c.to_i    # 14
puts c.to_f    # 14.6
puts c.to_r    # 73/5
puts c.to_c    # 14.6+0i
```

Some of them will even understand the letter `e` marking exponent in the String:

```
e = "2.3e4x5"
puts e         # 2.3e4x5
puts e.to_i    # 2
puts e.to_f    # 23000.0
puts e.to_r    # 23000/1
puts e.to_c    # 23000.0+0i
```

## Full example

```ruby
{{#include examples/ruby/string_to_number.rb }}
```


## Comments

foo.to_i" works for simple cases. One might consider: "Integer(foo)".

"1.4.5".to_i => 1
Integer("1.4.5") => invalid value for Integer()

Latter is better suited as a result.

<hr>

Hi, in this case my string is "12345.678" when use to_f then result is: 12345.67 (only 2 number after dot)
How can i get enough 12345.678 . I mean how can i get more number after dot.
Thanks guys

timestamp: 2015-11-02T15:00:01
tags:
  - String
  - to_i
  - to_f
  - to_r
  - +
  - base

