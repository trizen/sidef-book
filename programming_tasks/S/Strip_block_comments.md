[1]: https://rosettacode.org/wiki/Strip_block_comments

# [Strip block comments][1]

For extra credit, it allows the caller to redefine the delimiters.

```ruby
func strip_block_comments(code, beg='/*', end='*/') {
    var re = Regex(beg.escape + '.*?' + end.escape, 's')
    code.gsub(re, '')
}
 
say strip_block_comments(ARGF.slurp)
```
