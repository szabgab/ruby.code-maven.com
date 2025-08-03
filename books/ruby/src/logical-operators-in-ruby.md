# Logical operators in Ruby (and, or, not), (&&, ||, !)


In Ruby there are two sets of logical operators:

`and`, `or`, `not`

`&&`, `||`, `!`


Normally you can use either set of the operators but it is not recommended to mix
them in the same expression. The difference between the two sets is the precedence.
The operators that are words (and, or, not) are lower in the operator precedence table
than the other three.

Logical operators are used in a conditional expression, for example in an `if`
statement or in the Ternary operatory, we would like to combine 2 ore more conditions.

For example we would like to check if the `age` of the user is bigger that 18, but smaller than 23.

We can write:

`18 < age and age < 23`

The same can also be written as

`18 < age && age < 23`

There is no real difference between the two expressions. The `&&` are there mostly for historical reasons
as they were used in many programming languages before Ruby. `and` is usually much more readable.


```ruby
{{#include examples/ruby/logical_operators.rb }}
```

timestamp: 2019-04-16T16:44:01
tags:
  - and
  - &&

