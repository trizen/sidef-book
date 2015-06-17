[1]: http://rosettacode.org/wiki/Create_a_file

# [Create a file][1]

```ruby
# Here
%f'output.txt' -> create;
%d'docs'       -> create;
 
# Root dir
Dir.root + %f'output.txt' -> create;
Dir.root + %d'docs'       -> create;
```