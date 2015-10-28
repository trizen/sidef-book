[1]: http://rosettacode.org/wiki/FizzBuzz

# [FizzBuzz][1]

```ruby
{ |i|
    if (i %% 3) {
        print "Fizz";
        i %% 5 && print "Buzz";
        print "\n";
    }
    elsif (i %% 5) { say "Buzz" }
    else  { say i };
} * 100;
```


Shorter solution:

```ruby
{|i|say "#{<Fizz>[i%3]}#{<Buzz>[i%5]}"||i}*100;
```