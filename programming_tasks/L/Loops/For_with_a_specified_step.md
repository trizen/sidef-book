[1]: http://rosettacode.org/wiki/Loops/For_with_a_specified_step

# [Loops/For with a specified step][1]

```ruby
for (var i = 2; i <= 8; i += 2) {
    say i;
}
```


Alternatively, by using ranges:

```ruby
2.to(8).by(2).each { |i|
    say i;
}
```


Or:

```ruby
range(2, 8, 2).each { |i|
    say i;
}
```