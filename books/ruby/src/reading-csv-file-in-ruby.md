# Reading CSV file in Ruby


Ruby comes with a standard library called [CSV](http://ruby-doc.org/stdlib-2.0.0/libdoc/csv/rdoc/CSV.html) to make it easy to read
files with Comman Separated values


## CSV file

In this CSV file the 3rd fields in every "row" is a number. We would like to sum these numbers.

```ruby
{{#include examples/data/distance.csv }}
```

If it was a simpler file We could read it line-by-line and use `split` to cut it into parts,
but in this file there is a field that has a comman in it. Plain `split` would not be able to
handle the field enclosed in quote marks `"` containing a comma.

This file also has a field with an embedded newline. So the physical rows of the file, marked by `\n` newlines
are not the same as the logical lines that and good CSV parser would understand.

```ruby
{{#include examples/ruby/add_third_column.rb }}
```

In this example first we <b>load the CVS module</b> then we use the `CVS.foreach(filename)` construct
to iterate over the file loical row by logical row. On each iteration the variable `row` is going to be
an array. The third element can be accessed using index 2.  We have to convert the value to a number using
`to_i` and then we can add it to the variable `sum`

timestamp: 2015-10-09T16:30:01
tags:
  - CSV

