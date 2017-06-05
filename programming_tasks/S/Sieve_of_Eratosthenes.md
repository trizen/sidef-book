[1]: http://rosettacode.org/wiki/Sieve_of_Eratosthenes

# [Sieve of Eratosthenes][1]

```ruby
func sieve(limit) {
    var sieve_arr = [false, false, (limit-1).of(true)...]
    gather {
        sieve_arr.each_kv { |number, is_prime|
            if (is_prime) {
                take(number)
                for i in (number**2 .. limit `by` number) {
                    sieve_arr[i] = false
                }
            }
        }
    }
}

say sieve(100).join(",")
```

#### Output:
```
2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97
```

Alternative implementation:
```ruby
func sieve(limit) {
    var composite = []
    for n in (2 .. limit.isqrt) {
        for i in (n**2 .. limit `by` n) {
            composite[i] = true
        }
    }
    2..limit -> grep{ !composite[_] }
}

say sieve(100).join(",")
```
