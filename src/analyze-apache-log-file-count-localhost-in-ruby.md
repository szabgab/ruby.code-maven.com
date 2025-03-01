# Analyze Apache log file - count localhost in Ruby


The [exercise](/exercise-analyze-apache-log-file-count-localhost) was, that give a log file created by the Apache web server (or for that matter by any web server), to
count how many hits arrived from localhost (IP 127.0.0.1) and how many have arrived from any other place.


The log file look like this:

```ruby
{{#include examples/data/apache_access.log }}
```

## The Algorithm:

We need two counters, one for counting the hits from 127.0.0.1 and one to count all the other hits.
Then we need to go over all the lines. Extract the IP address, and based on its value to increment one
of the counters.


We expect the program to be used as `ruby apache_localhost.rb  data/apache_access.log`.
That is, we expect the user to provide the name of the Apache log file as a parameter on the command line.

Therefore in the first few lines we check if the user has supplied any filename on the command line by checking
the [number of elements in ARGV](/argv-the-command-line-arguments-in-ruby). If the given number of
parameters is not 1, then we tell the user how to use our program and `exit`.

Then we copy the name of the file from `ARGV` to an internal variable called `filename`. Mostly for readability of the code.

Then we create the two counters and initialize them to 0.

The we [open the file for reading](/open-file-and-read-content-in-ruby) and read it line-by-line using `each`.
On each iteration the variable `line` will hold the current line form the file.

The IP address is the first value in every row up till the first space.
There are a number of ways to extract it from the line. In this case we used the `index` method on the `line`
passing a space to it. That will return the location of the first space in the `line`. Because the string indexing starts with 0,
this number will be also the length of the IP address. Hence we have assigned the result to a variable called `length`.

We can use this variable then to extract the substring from the `line` that starts on character 0 and includes `length` characters.
We can do that by providing the index of the beginning of the substring and the length of the substring we would like to extract.
That will be the IP address from the current line.

What remains is to check if this equals to 127.0.0.1 (localhost) and increment the appropriate counter.

```ruby
{{#include examples/ruby/apache_localhost.rb }}
```

timestamp: 2015-10-27T08:30:01
tags:
  - index
  - substr
  - open
  - ARGV
  - []

