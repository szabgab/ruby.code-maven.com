# The conditional operator in Ruby

The official name of the `? :` operator is the [conditional operator](https://en.wikipedia.org/wiki/%3F:),
though most people know it as the **ternary operator** indicating the number of operands it has.


There are several **unary operators** that handle a single operand. For example `-` can be unary operator.

Most of the operators ad **binary operators** that handle two operands. For example `*` always needs two operands to
work on, but in most cases `-` is also used as a binary operatory.

There is only one **ternary operator**, that has 3 operands. It is called the **conditional operator**, but because
it is the only one with 3 operands, most of the people call it **the ternary operator**.


## Conditional Operator in Ruby

In general it looks like this:

```
CONDITION ? EVALUATE_IF_CONDITION_WAS_TRUE : EVALUATE_IF_CONDITION_WAS_FALSE
```

It evaluates the `CONDITION`. If it is `true` then the code evaluates the part between `?` and `:` and returns the result.
If the `CONDITION` is false, then the middle part is skipped and the 3rd part is evaluated and the result of that expression is returned.

## Example puts

In this example the return value of the conditional operator is passed to `puts`

```
filename = ARGV.shift
puts filename ? filename : 'No file given'
```

## Example smaller

In this example we check whihc one of the two random values is smaller and return that one:

```ruby
{{#include examples/ruby/smaller_ternary.rb }}
```

timestamp: 2015-10-31T14:23:23
tags:
  - ?:

