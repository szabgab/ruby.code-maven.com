# Variables and Variable Interpolation in Ruby

Using simple values as in [introduction to Ruby](/getting-started-with-ruby) article will get you bored soon. It is much more interesting
to create names that can hold values and then use those names. These names we call "variables", because usually their content can be changes.


Variable nanes can starte with any lower~ or uppercase letter or underscore. They can contain lowercase, uppercase letters, digits, and underscores.
Once we have assigned value to a variable we can use `puts` to print the content of the variable


We can also use the variables for other operations. For example to add them together:

```ruby
{{#include examples/ruby/add_numbers.rb }}
```

```
$ ruby add_numbers.rb
42
```


With this we can create a variable containing the name of the user, and then welcome that user by <b>concatenating</b> together
two strings and the variable using `+` as string addition.

```ruby
{{#include examples/ruby/hello_name.rb }}
```

```
$ ruby hello_name.rb
Hello Foo Bar, how are you?
```

## Interpolation or variable embedding

There is however another way to create the same result:

```ruby
{{#include examples/ruby/hello_name_embedded.rb }}
```


Here we used the `#{}` construct to tell ruby, instead of the word 'name' it needs to take the content of the variable called 'name'
and include that in the string.

## Variable declaration in Ruby

In Ruby there is no need to <b>declare</b> a variable. It just has to appear in an assignment before it is used in any other expression.

```ruby
{{#include examples/ruby/bad_variable.rb }}
```

```
$ ruby bad_variable.rb
23
bad_variable.rb:5:in `<main>': undefined local variable or method `y' for main:Object (NameError)
```


timestamp: 2015-10-06T10:50:01
tags:
  - puts
  - +
  - #{}

