[1]: http://rosettacode.org/wiki/Empty_directory

# [Empty directory][1]

Built-in method:

```ruby
Dir.new('/my/dir').is_empty;    # true, false or nil
```


User-defined function:

```ruby
func is_empty(dir) {
    dir.open(\var dir_h) || return nil;
    dir_h.each { |file|
        file ~~ ['.', '..'] && next;
        return false;
    };
    return true;
};
```