[1]: http://rosettacode.org/wiki/Loops/Continue

# [Loops/Continue][1]

```ruby
for (1..10) { |i|
    print i;
    if (i % 5 == 0) {
        print "\n";
        next;
    };
    print ', ';
}
```
