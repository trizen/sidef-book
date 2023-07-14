[1]: https://rosettacode.org/wiki/Check_that_file_exists

# [Check that file exists][1]

```ruby
# Here
say (Dir.cwd  + %f'input.txt' -> is_file)
say (Dir.cwd  + %d'docs'      -> is_dir)
 
# Root
say (Dir.root + %f'input.txt' -> is_file)
say (Dir.root + %d'docs'      -> is_dir)
```


NOTE: To check only for existence, use the method _exists_
