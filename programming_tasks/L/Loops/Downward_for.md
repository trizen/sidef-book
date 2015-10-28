[1]: http://rosettacode.org/wiki/Loops/Downward_for

# [Loops/Downward for][1]

```ruby
for (var i = 10; i >= 0; i--) {
    say i;
}
```


Idiomatic:

```ruby
10.downto(0).each { |i|
    say i;
}
```