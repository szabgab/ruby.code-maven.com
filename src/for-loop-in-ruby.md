# For loop in Ruby (iterating over array elements)

In Ruby the C-like for-loop is not in use. Instead of that people usually iterate over the elements of an array using
the `each` method.


```ruby
{{#include examples/ruby/iterating_on_array.rb }}
```

In this example we have an array with 3 elements. At first we just printed the array as it is. We got the values
on on every line. That can be useful for debugging, but it we want to go over the elements we need some kind of a loop.

The `each` method allows us to iterate over the elements of the array. On every iteration the variable between the
pipes (`item` in our case) will receive the current value.

Here we have 2 examples. The first one uses curly braces to mark the beginning and the end of the block,
the other one uses the `do - end` pair.

```
$ ruby examples/ruby/iterating_on_array.rb 
Foo
Bar
Baz

Foo
Bar
Baz

Foo
Bar
Baz
```


## A 'for' loop that is not recommended

There is another way to iterate over the elements, but it can have a nasty side-effect and thus not recommended.

```ruby
{{#include examples/ruby/for_loop_on_array.rb }}
```

the code looks ok, the result is ok

```
$ ruby examples/ruby/for_loop_on_array.rb 
Foo
Bar
Baz
```

But if we have used the `item` variable earlier, then this `for` loop will overwrite that
other `item` variable with the last value seen in the loop.

```ruby
{{#include examples/ruby/for_loop_on_array_global.rb }}
```

Note how, after the loop has finished the variable `item` holds 'Baz'.

```
$ ruby examples/ruby/for_loop_on_array_global.rb 
Foo
Bar
Baz

Baz
```

timestamp: 2015-02-10T13:00:01
tags:
  - each
  - for

