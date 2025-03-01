# Count digits in Ruby

In this exercise we had to [count digits in a file](/exercise-count-digits).


## The algorightm

We need to go over the file line-by-line.
For each line then we need to go over it character-by-character. If it is a digit, we need to increment the appropriate counter.
We could use 10 different variables (c0, c1, ... c9) to count the number of occurances of the respective digits, but there is
a much more comfortable solution using [arrays](/ruby-arrays). Specifically we use an array called `count` with 10 elements in it.
In `count[0]` we will count the number 0s, in `count[1]` we will count the number of 1s, ...
up till `count[9]` in which we will count the number of 9s.

## The solution in Ruby

In this solution written in [Ruby](/ruby), we start by getting the name of the file to be process on the command line.

At first we check if [ARGV](/argv-the-command-line-arguments-in-ruby) has the right number of arguments.
If not we print an error message and `exit`.

Then we declare the `count` array.

Get the name of the file from the first element of the `ARGV` array containing the values from the command line
and [open it for reading](/open-file-and-read-content-in-ruby) and iterate over
it using `each`.

In each iteration  `line` will contain a single line. We need to go over it character-by-character.
There are a number of ways to do this. In this solution I've decided to split the string into individual characters and
then to iterate over the characters.

Using the [split](/ruby-split) method with an empty string we cut up the string at every place where the empty string matches.
Meaning we split up the string between any two charctes. The result is a list of charcters assigned to the `chars` array.

Then we [iterate over the elements of this array](/for-loop-in-ruby). In each iteration `c`
is a single character from the source file. Based on our assumption, it is either a digit (0-9) or space.

If it is not a space `if c != ' ' then` we would like to increment the appropriate counter.

If this is our first encounter with the particular digit we need to initialize the array element that
will count that digit.

```
if not count[c.to_i] then
    count[c.to_i] = 0
end
```

Then in every case we increment it by one using the following expression:

```
count[c.to_i] += 1
```

At the end of the loop we have counted all the digits. We need to display the results.

For that we iterate over all the numbers between 0 and 9 and print out the number, and the counter of that number.

We could have printed the content of `count[i]</hl< directly, but then we would have holes for the digits
that don't appear in our source. (In this case 4 and 6). That would not look right. Any observer would think there is
a bug in the code. It is much better to print 0 if the digit never appeared. We do that by using 
the [conditional operator](/conditional-operator-in-ruby).

```ruby
{{#include examples/ruby/count_digits.rb }}
```

timestamp: 2015-11-03T22:23:23
tags:
  - open
  - split
  - +=

