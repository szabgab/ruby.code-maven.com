Arrays in Ruby


Arrays in Ruby are similar to [arrays in Perl](https://perlmaven.com/perl-arrays) and lists in Python.
They can hold a bunch of unrelated values in slots indexed from 0 up.

Similar to the other two dynamic languages, arrays in ruby can also grow and shrink as the user needs them.
There is no need for special memory handling.


Arrays in Ruby are created by comma separated values assigned to a variable:

```
names = 'Foo', 'Bar', 'Baz'
```

We can access them using an index after the name of the variable:

```
puts names[0]    # Foo
puts names[1]    # Bar
puts names[2]    # Baz
```

We can fetch the size of the array, by using the `length` method:

```
puts names.length   # 3
```

If we try to access an element by an index that is not in the array, Ruby will print nothing (an empty sting):

```
puts names[3]       # (nothing)
```


On the other hand, just like in Perl, Ruby arrays understand negative indexes. They access the array from the other end:

```
puts names[-1]      # Baz
```

## Assign to array element

We can assign a value to any of the indexes in the array. It overwrites the old value.
Then we can fetch the current value from the array.

```
names[1] = 'Happy'
puts names[1]     # Happy
```

Not only that, but we can also assign to indexes that were not part of the array previously. The array will automatically grow as
we can see from the value returned by the `length` method.

```
names[3] = 'Moo'
puts names[3]       # Moo
puts names.length   # 4
```

We can even assign value to an index further away. The array will be enlarged and the intermediate elements will remain empty.
(They will have `nil` in them.)

```
names[6] = 'Far Away'
puts names[6]       # Far Away
puts names.length   # 7
puts names[5]       # (nothing)
```


## Going over the elements of the array

There are a number of ways to [iterate over the elements of an array](/for-loop-in-ruby).

## Pretty Print values for debugging

Similar to the [Data::Dumper module in Perl](https://perlmaven.com/debugging-perl-scripts),
Ruby has the `pp` library for Pretty Printing data structures.
It makes it easy to print out the content of an array:

```
require 'pp'
pp names        # ["Foo", "Happy", "Baz", "Moo", nil, nil, "Far Away"]
```

## push

If we want to add one or more elements to an array, we can use the `push` method to do that.

```
names.push 'Hello', 'World'
pp names     # ["Foo", "Happy", "Baz", "Moo", nil, nil, "Far Away", "Hello", "World"]
```


## pop

The opposite operation is called `pop`. It will fetch the last element of an array,
remove it from the array and return it to be used in an assignment:

```
last = names.pop
pp names    # ["Foo", "Happy", "Baz", "Moo", nil, nil, "Far Away", "Hello"]
puts last   # World
pp last     # "World"
```

We can even pass a parameter to `pop` to indicate how many element we wish to remove from the end of the array.
In that case (even if we passed 1), the returned value will be an array of the removed elements:

```
last = names.pop 2
pp names    # ["Foo", "Happy", "Baz", "Moo", nil, nil]
pp last     # ["Far Away", "Hello"]
```

## shift

`shift` moves the content of the array to the left. The left-most element is removed from the array and
returned to be used in an assignment (or any other operation). It can be thought as similar to `pop`
just at the beginning of the array.

```
first = names.shift
pp names    # ["Happy", "Baz", "Moo", nil, nil]
puts first  # Foo
```

## unshift

`unshift` is the opposite of `shift`. It puts one or more elements to the
beginning of the array. This methods is rarely used.

```
names.unshift 'Zorg', 'Morg'
pp names    # ["Zorg", "Morg", "Happy", "Baz", "Moo", nil, nil]
```

## Full example

```ruby
{{#include examples/ruby/array.rb }}
```


timestamp: 2015-10-29T14:31:23
tags:
  - []
  - array
  - push
  - pop
  - shift
  - unshift

