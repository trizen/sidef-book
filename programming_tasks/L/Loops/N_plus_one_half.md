[1]: http://rosettacode.org/wiki/Loops/N_plus_one_half

# [Loops/N plus one half][1]

```ruby
for 1..10 { |i|
    print i;
    i == 10 && break;
    print ', ';
}
 
print "\n";
```