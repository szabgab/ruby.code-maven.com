# Solution: Number guessing game in Ruby

In this [exercise](/exercises), you were asked to create the first version of the
[Number guessing game](/exercise-number-guessing-game). We are going to see a solution
in Ruby.


```ruby
{{#include examples/ruby/number_guessing.rb }}
```

We use the `rand` function to generate a random number. If we called it without any parameter,
`rand` would return a floating point number between 0 and 1.
As we passed a whole number to it, the `rand` function generated a whole number between
0 and 200, the number we gave.

There is a commented out line printing the hidden value back. I used it to be able to test the code
which was comparing my input to the hidden number.

Then we use the `print` function to ask the user to type in a number. We use the
`print` functions instead of the `puts` function to avoid adding a trailing newline.
So the cursor will appear on the same line where the request was printed.

`gets` reads in whatever we type in response. `to_i` converts it to integer. (By default when
we read in something from the standard input, that will be a string. Even if it only contains numbers.
We have to tell Ruby to convert it to an integer.)

Then we have 3 cases depending the relative values of the `hidden` and `guess` variables.

timestamp: 2015-10-18T11:00:01
tags:
  - exercises
  - rand
  - gets
  - print
  - puts
  - if
  - elsif
  - else

