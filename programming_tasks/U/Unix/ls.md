[1]: http://rosettacode.org/wiki/Unix/ls

# [Unix/ls][1]

Explicit, by opening the current working directory:

```ruby
var content = [];
Dir.cwd.open.each { |file|
    file ~~ < . .. > && next;
    content.append(file);
};
 
content.sort.each { |file|
    say file;
};
```


Implicit, by using the _String.glob_ method:

```ruby
'*'.glob.each { |file|
    say file;
};
```