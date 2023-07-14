[1]: https://rosettacode.org/wiki/Repeat

# [Repeat][1]

```ruby
func repeat(f, n) {
    { f() } * n
}
 
func example {
    say "Example"
}
 
repeat(example, 4)
```
