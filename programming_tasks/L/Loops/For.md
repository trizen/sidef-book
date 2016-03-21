[1]: http://rosettacode.org/wiki/Loops/For

# [Loops/For][1]

*for(;;)* loop:

```ruby
for (var i = 1; i <= 5; i++) {
    for (var j = 1; j <= i; j++) {
        print '*'
    }
    print "\n"
}
```


*for([])* loop:

```ruby
for (1..5) { |i|
    for (1..i) { print '*' }
    print "\n"
}
```


*for-in* loop:

```ruby
for i in (1..5) {
    for j in (1..i) { print '*' }
    print "\n"
}
```

Idiomatic:

```ruby
5.times { |i|
    i.times { print '*' }
    print "\n"
}
```
