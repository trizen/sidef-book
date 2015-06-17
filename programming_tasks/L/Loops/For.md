[1]: http://rosettacode.org/wiki/Loops/For

# [Loops/For][1]

*for(;;)* loop:

```ruby
for (var i = 1; i <= 5; i++) {
    for (var j = 1; j <= i; j++) {
        print '*';
    };
    print "\n";
}
```


*for([])* loop:

```ruby
for (1..5) { |i|
    for (1..i) { print '*' };
    print "\n";
}
```


Alternatively:

```ruby
for (1..5) { |i|
    for (i..5) { |j|
        say '*'*j; break;
    }
}
```