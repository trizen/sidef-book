[1]: https://rosettacode.org/wiki/Loops/Downward_for

# [Loops/Downward for][1]

*for(;;)* loop:

```ruby
for (var i = 10; i >= 0; i--) {
    say i
}
```

*for-in* loop:

```ruby
for i in (11 ^.. 0) {
    say i
}
```

*.each* method:

```ruby
10.downto(0).each { |i|
    say i
}
```
