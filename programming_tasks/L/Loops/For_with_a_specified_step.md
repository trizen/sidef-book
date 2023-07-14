[1]: https://rosettacode.org/wiki/Loops/For_with_a_specified_step

# [Loops/For with a specified step][1]

*for(;;)* loop:

```ruby
for (var i = 2; i <= 8; i += 2) {
    say i
}
```

*for-in* loop:

```ruby
for i in (2 .. (8, 2)) {
    say i
}
```

*.each* method:

```ruby
2.to(8).by(2).each { |i|
    say i
}
```
