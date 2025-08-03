# Iterate over characters of a string in Ruby

Sometimes, given a string, I need to go over it character by character. It can easily be done after using `split`
to cut up the sting or by using the `each_char` method.


In the first example we first split the string using the empty string as separator. That it,
we want to cut the string every place where we find an empty sting in it. In other words every character.

```ruby
{{#include examples/ruby/iterate_characters_split.rb }}
```

The resulting array has 6 elements in it as returned by the `length` method and the third
character (index 2) is the letter `c`. I added these just so we can see the result of `split`
really behaves as an array.

Finally we use the `each` method to iterate over the elements of the array that are the characters of
the original string. See the [for loop in Ruby](/for-loop-in-ruby) for an explanation about the loop.

```
$ ruby examples/ruby/iterate_characters_split.rb
6
c

a
b
c
d
e
f
```


## split without temporary variable

In the second example we use the same `split` method, but this time we called the `each`
method right on top of the result received from `split`:

```ruby
{{#include examples/ruby/iterate_characters.rb }}
```

The result, not surprisingly, is the same as earlier:

```
$ ruby examples/ruby/iterate_characters.rb 
a
b
c
d
e
f
```

## each_char to simplify

In order to make it even more simple, Ruby supplies a method called `each_char` that will
do all the work:

```ruby
{{#include examples/ruby/iterate_characters_each_char.rb }}
```

```
$ ruby examples/ruby/iterate_characters_each_char.rb
a
b
c
d
e
f
```

## Comments

so would it be accurate to write:

```
%w { 1 2 3 4 }.each do |num|
s3_file "/usr/local/tomcat7-7/part[num].tif"
remote_path "part[num].tif"
bucket "perftest-data"
aws_access_key_id "XXXXXXX"
aws_secret_access_key "ZZZZZZZZ"
owner "root"
group "root"
mode "0644"
action :create
end
```

---

You can also do it with a simple iteration loop, leveraging the fact that string objects are stored as arrays of characters:

```
input = 'abcdef'

input.length.times { |i| 
   puts input[i] 
}
```



timestamp: 2015-02-11T15:30:01
tags:
  - split
  - each_char

