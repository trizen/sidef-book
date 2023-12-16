[1]: https://rosettacode.org/wiki/Erdős-Nicolas_numbers

# [Erdős-Nicolas numbers][1]

```ruby
func is_Erdős_Nicolas(n) {

    n.is_abundant || return false

    var sum   = 0
    var count = 0

    n.divisors.each {|d|
        ++count;         sum += d
        return count if (sum == n)
        return false if (sum >  n)
    }
}

var count = 8   # how many terms to compute

^Inf -> by(2).each {|n|
    if (is_Erdős_Nicolas(n)) { |v|
        say "#{'%8s'%n} is the sum of its first #{'%3s'%v} divisors"
        --count || break
    }
}
```

#### Output:
```
      24 is the sum of its first   6 divisors
    2016 is the sum of its first  31 divisors
    8190 is the sum of its first  43 divisors
   42336 is the sum of its first  66 divisors
   45864 is the sum of its first  66 divisors
  392448 is the sum of its first  68 divisors
  714240 is the sum of its first 113 divisors
 1571328 is the sum of its first 115 divisors
```
