# How to convert a string to UPPERCASE or lowercase in Ruby?

Ruby strings have methods to convert them to uppercase and lowercase. The method names
of the methods are `upcase` and `downcase` respectively.


Calling the `downcase` or `upcase` method on a string will return the lowercase or uppercase
version of the string, but the original variable won't change.

```
name = 'Ruby'
puts name           # Ruby
puts name.downcase  # ruby
puts name.upcase    # RUBY
puts name           # Ruby
```

Calling the same methods followed by an exclamation mark will both return lowercase/uppercase version
of the string and will also change the content of the variable.

```
puts name.downcase! # ruby
puts name           # ruby

puts name.upcase!   # RUBY
puts name           # RUBY
```

## Full example

```ruby
{{#include examples/ruby/case.rb }}
```

## Comments

Should not the output is based on name = 'Foo'?

----

Yes, it is but I'm sure that wasn't important in this case.

----

    For most folk not especially, we get the intent... but imagine just starting to learn programming for the first time... what you see and what you expect are different, and you could get confused.


---

You did a good job. I think many people will benefit from this post.

timestamp: 2015-10-29T19:30:01
tags:
  - uppercase
  - lowercase
  - uc
  - lc
  - to_lower
  - to_upper
  - downcase
  - upcase

