[1]: http://rosettacode.org/wiki/Rename_a_file

# [Rename a file][1]

```ruby
# Here
File.rename('input.txt', 'output.txt');
File.rename('docs',      'mydocs');
 
# Root dir
File.rename(Dir.root + %f'input.txt', Dir.root + %f'output.txt');
File.rename(Dir.root + %f'docs',      Dir.root + %f'mydocs');
```