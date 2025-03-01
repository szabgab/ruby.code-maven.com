# Solution: Sum of numbers in a file implemented in Ruby

The exercise was to take a file where each line contains a number and display the [sum of the numbers in the file](/exercise-sum-of-numbers-in-file).


We have the name of the file in a variable called `filename` and we create anothe variable called `sum`
where we are going to hold the sum of the numbers. We initialize it to 0.

Then we open the file, by default, for reading and get back the filehandle.

Using an `each` loop we can iterate over the lines of the file. In each iteration the content of the current line
is in the variable called `line`. Even though we expect it to be a number, what Ruby read in is kept as 
[String](/basic-data-structures-in-ruby). We need to convert it into a number, an integer number in this case,
using the `to_i` method. We can then add the number to the content of `sum` using the `+=` operator.

After the loop is finished, when we don't have anything else to do with the file, we should call the `close` method
to close the file.

At the end we print out the content of `sum`

```ruby
{{#include examples/ruby/sum_numbers_in_file.rb }}
```

## Sum of numbers using a one-liner

There is another solution, using some more advanced techniques in Ruby:

Here the whole expression computing the sum is embedded ina string. The final result
of this expression will be included in the print.

```ruby
{{#include examples/ruby/sum_numbers_in_file_oneliner.rb }}
```

Inside the string we have the following expression:

`open(filename).readlines.map(&:to_i).reduce :+`

Let's take that apart. The first statement is `open(filename)`. It opens the file for reading
and returns a filehandle.

Instead of assigning it to variable though. we immediately use this filehandle and call the `readlines` method of it.

the `readlines` method will return a an array of the lines. Each line in the original file is an element in
the returned array.

The  `map` method will go over each element of the array and call the given function on each element.
Specifically it will call `to_i` on each element of the array converting each element into a number.
So the `map` method will already return an array of numbers.

In the last section we call the `reduce` method. It reduces the array to a single element by executing the
expression `+` on every two element. More specifically it takes the first two calues and executes the statement (`+`)
on these two. Then it takes the resul of this and the next element (the third element) and executes it again adding them together.
Then it takes the result of this and the next element (the 4th). etc. Effectively it means putting `+` between all the elements
and calculating their sum.


```ruby
{{#include examples/ruby/sum_numbers_in_file_oneliner_explained.rb }}
```

timestamp: 2015-10-20T16:00:01
tags:
  - open
  - each
  - to_i
  - map
  - reduce

