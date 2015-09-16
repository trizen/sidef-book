[1]: http://rosettacode.org/wiki/FizzBuzz

# [FizzBuzz][1]

```ruby
{ |i|
    if (3.divides(i)) {
        print "Fizz";
        5.divides(i) && print "Buzz";
        print "\n";
    }
    elsif (5.divides(i)) { say "Buzz" }
    else  { say i };
} * 100;
```


Shorter solution:

```ruby
{|i|say "#{<Fizz>[i%3]}#{<Buzz>[i%5]}"||i}*100;
```
