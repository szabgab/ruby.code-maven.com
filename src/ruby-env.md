# Ruby ENV - access the environment variables

Ruby maintaines a hash called [ENV](http://ruby-doc.org/core-2.1.4/ENV.html) that gives us access to the
envrionment variables such as PATH or HOME.


We can see them all using [pp, the pretty printer of Ruby](/display-complex-data-structure-in-ruby).

```ruby
{{#include examples/ruby/env.rb }}
```

We can also access the value directly. For example: `puts ENV['PATH']`, we can add new environment variables or change existing ones with
one big caveat. Once our Ruby program ends these changes will be gone.

If we start a new process from our Ruby program after we have made modifications `ENV`, all those modifications
will be seen by the other process.  However the changes cannot propagate to the process that launched our Ruby program:

For example if run this program:

```ruby
{{#include examples/ruby/change_path_and_system.rb }}
```

The output will look something like this:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
/nothing/here
```

The first time we called `system` the new shell saw the original content of the `PATH` environment variable.
Then we changed it and set it to something horribly bad.
When we called `system` the second time the new shell saw the new value.

After tunning the above script execute the following in the Unix/Linux shell

```
echo $PATH
```

It will print the same path as it did with the first call to `system`.

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

This means our changes in the Ruby code have not changed the environment variable for the parent process.

This is a feature of most or all of the Operating Systems.

timestamp: 2015-11-18T15:50:01
tags:
  - ENV
  - system

