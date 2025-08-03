# How to write to file in Ruby


Writing to a file is quite simple in Ruby. The [File](http://ruby-doc.org/core-2.2.3/File.html) library helps us in it.


## Write to file

```ruby
{{#include examples/ruby/write_to_file.rb }}
```

If we run this it will create the file `out.txt` if it did not exists before or it will overwrite it if it existed earlier.
Any previous content will be removed.


## Append to file

If the second parameter to the `new` method is `'a'` and not `'w'` then we are goint to append to the
end of the file. This mean is the file already has some content, it will be kept and anything new will be added to the end.
If the file did not exist earlier then this too will create it.

```ruby
{{#include examples/ruby/append_to_file.rb }}
```

timestamp: 2015-11-21T08:30:01
tags:
  - File
  - write

