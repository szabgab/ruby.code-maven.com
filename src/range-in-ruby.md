# Range in Ruby


Ruby has two operators to generate a range of values. `..` is inclusive and `...` is exclusive.


## ..

```ruby
{{#include examples/ruby/range_two.rb }}
```

Will generate

```
0
1
2
3
```

including the beginning and the end similar to how the range in Perl works.

## ...

If we use 3 dots instead of two, then the range
will include the lower limit, but not the higher limit.
Similar to how `range` in Python works.

```ruby
{{#include examples/ruby/range_three.rb }}
```

```
0
1
2
```


## reverse range

If the limit on the left hand side is higher than on the right hand side,
the range operator won't return any values.

```ruby
{{#include examples/ruby/range_two_wrong.rb }}
```

It does not return any value.

As an alternative we can create a growing list of number and then call the `reverse` method on them.
For this however first we need to convert the rnage to an array:

```ruby
{{#include examples/ruby/range_two_reverse.rb }}
```

printing:

```
7
6
5
4
```


## Range of letters

In additonal to ceating ranges of numbers, Ruby can also create a range of letters:

```ruby
{{#include examples/ruby/range_letters.rb }}
```

```
a
b
c
d
```

## Range of characters

Not only that, but we can use any two characters in the visible part of the ASCII table:

```ruby
{{#include examples/ruby/range_chars.rb }}
```

```
Z
[
\
]
^
_
`
a
```


## Range with variables

We can also use variables as the lower and upper limits:

```ruby
{{#include examples/ruby/range_var.rb }}
```

timestamp: 2015-09-24T23:30:01
tags:
  - ..
  - ...
  - to_a
  - reverse

