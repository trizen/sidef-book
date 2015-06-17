[1]: http://rosettacode.org/wiki/Globally_replace_text_in_several_files

# [Globally replace text in several files][1]

```ruby
var files = %w(
                a.txt
                b.txt
                c.txt
              );
 
files.map{.toFile}.each { |file|
    say file.edit { |line|
        line.gsub("Goodbye London!", "Hello New York!");
    };
}
```