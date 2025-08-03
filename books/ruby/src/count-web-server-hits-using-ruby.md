# Count web server hits using Ruby


The [exercise](/exercise-analyze-apache-log-file-count-localhost) was, that given a log file created by the Apache web server (or by any web server), to
count how many hits arrived from each individual IP address.


Earlier we saw a solution in which we [counted the number of hits to locl host vs any other address](/analyze-apache-log-file-count-localhost-in-ruby).
That program already had the part that read the file line-by-line and extracted the IP address.

This time we just need to change the method of counting.
Instead of having two counters, one for the local and one for the remote IPs, we need to create an unknown number of counters.
We could do that using two arrays, but that would be complicated and slow.

Instead of that we use a hash. (Called a dictionary in Python and also called hash in Perl.)
In that hash the keys are going to be the IPs and the values are going to be the number of time the specific IP was seen.

A hash can start out empty and grow dynamically.

So we created an empty hash called `count`. We [open the file](/open-file-and-read-content-in-ruby), iterate over it line-by-line.
Locate the first space that's just after the IP address and use the returned value to fetch the IP address.
Now that we have the current IP address in a variable we can check if this is the first time we see it,
by asking if it the value of it is "true". If it is we increment it by 1. If this is the first time we
see the word we add it as a key to the hash and initialize its value to be 1.

That's the whole story.

In the last 3 lines we iterate over all the key-value pairs in the hash and print the values.

```ruby
{{#include examples/ruby/apache_count_hits.rb }}
```

timestamp: 2015-10-30T13:30:01
tags:
  - index
  - substr
  - open
  - ARGV
  - []

