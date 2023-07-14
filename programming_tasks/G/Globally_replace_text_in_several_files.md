[1]: https://rosettacode.org/wiki/Globally_replace_text_in_several_files

# [Globally replace text in several files][1]

```ruby
var names = %w(
                a.txt
                b.txt
                c.txt
              )
 
names.map{ File(_) }.each { |file|
    say file.edit { |line|
        line.gsub("Goodbye London!", "Hello New York!")
    }
}
```
