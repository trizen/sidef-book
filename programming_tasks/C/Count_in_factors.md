[1]: https://rosettacode.org/wiki/Count_in_factors

# [Count in factors][1]

```ruby
class Counter {
    method factors(n, p=2) {
        var a = gather {
            while (n >= p*p) {
                while (p `divides` n) {
                    take(p)
                    n //= p
                }
                p = self.next_prime(p)
            }
        }
        (n > 1 || a.is_empty) ? (a << n) : a
    }
 
    method is_prime(n) {
        self.factors(n).len == 1
    }
 
    method next_prime(p) {
        do {
            p == 2 ? (p = 3) : (p+=2)
        } while (!self.is_prime(p))
        return p
    }
}
 
for i in (1..100) {
    say "#{i} = #{Counter().factors(i).join(' × ')}"
}
```
