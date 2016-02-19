[1]: http://rosettacode.org/wiki/Sieve_of_Eratosthenes

# [Sieve of Eratosthenes][1]

```ruby
func sieve(limit) {
    var sieve_arr = [false, false, [true]*(limit-1)...]
    gather {
        sieve_arr.each_kv { |number, is_prime|
            if (is_prime) {
                take(number)
                number.sqr.to(limit).by(number).each { |i|
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
