[1]: https://rosettacode.org/wiki/Loops/Continue

# [Loops/Continue][1]

```ruby
for i in (1..10) {
    print i
    if (i % 5 == 0) {
        print "\n"
        next
    }
    print ', '
}
```
