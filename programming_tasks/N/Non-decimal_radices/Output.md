[1]: http://rosettacode.org/wiki/Non-decimal_radices/Output

# [Non-decimal radices/Output][1]

```ruby
range(0, 33).each { |n|
    printf(" %6b %3o %2d %2X\n", ([n]*4)...);
}
```