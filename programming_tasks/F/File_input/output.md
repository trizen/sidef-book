[1]: http://rosettacode.org/wiki/File_input/output

# [File input/output][1]

```ruby
var in = %f'input.txt'.open_r;
var out = %f'output.txt'.open_w;
 
in.each { |line|
    out.print(line);
};
```