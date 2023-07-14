[1]: https://rosettacode.org/wiki/Walk_a_directory/Non-recursively

# [Walk a directory/Non-recursively][1]

```ruby
'*.p[lm]'.glob.each { |file| say file }    # Perl files under this directory
```

#### Output:
```
x.pl
x.pm
```
```ruby
func file_match(Block callback, pattern=/\.txt\z/, path=Dir.cwd) {
    path.open(\var dir_h) || return nil
    dir_h.entries.each { |entry|
        if (entry.basename ~~ pattern) {
            callback(entry)
        }
    }
}
 
file_match(
    path: %d'/tmp',
    pattern: /\.p[lm]\z/i,
    callback: { |file|
        say file;
    }
)
```

#### Output:
```
/tmp/x.pl
/tmp/x.pm
```
