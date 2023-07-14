[1]: https://rosettacode.org/wiki/FizzBuzz

# [FizzBuzz][1]

Structured:

```perl
{ |i|
    if (i %% 3) {
        print "Fizz"
        i %% 5 && print "Buzz"
        print "\n"
    }
    elsif (i %% 5) { say "Buzz" }
    else  { say i }
} << 1..100
```

Declarative:

```perl
func fizzbuzz({ _ %% 15 }) { "FizzBuzz" }
func fizzbuzz({ _ %%  5 }) {     "Buzz" }
func fizzbuzz({ _ %%  3 }) {     "Fizz" }
func fizzbuzz(        n  ) {          n }

for n in (1..100) { say fizzbuzz(n) }
```

One-liner:

```ruby
{>"#{<Fizz>[.%3]}#{<Buzz>[.%5]}"||_}<<1..100
```
