[1]: https://rosettacode.org/wiki/Summation_of_primes

# [Summation of primes][1]

Built-in:

```ruby
say sum_primes(2e6)  #=> 142913828922
```


Linear algorithm:

```ruby
func sum_primes(limit) {
    var sum = 0
    for (var p = 2; p < limit; p.next_prime!) {
        sum += p
    }
    return sum
}
 
say sum_primes(2e6)
```


Sublinear algorithm:

```ruby
func sum_of_primes(n) {
 
    return 0 if (n <= 1)
 
    var r = n.isqrt
    var V = (1..r -> map {|k| idiv(n,k) })
    V << range(V.last-1, 1, -1).to_a...
 
    var S = Hash(V.map{|k| (k, polygonal(k,3)) }...)
 
    for p in (2..r) {
        S{p} > S{p-1} || next
        var sp = S{p-1}
        var p2 = p*p
        V.each {|v|
            break if (v < p2)
            S{v} -= p*(S{idiv(v,p)} - sp)
        }
    }
 
    return S{n}-1
}
 
say sum_of_primes(2e6)
```

#### Output:
```
142913828922
```
