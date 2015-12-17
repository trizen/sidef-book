[1]: http://rosettacode.org/wiki/Sieve_of_Eratosthenes

# [Sieve of Eratosthenes][1]

```ruby
func sieve(limit) {
    var is_prime = [false, false, ([true] * limit-1)...];
    gather {
        is_prime.each_kv { |number, prime|
            if (prime) {
                take(number);
                number**2 ... limit -> each { |n| is_prime[n] = false if n%%number }
            }
        }
    }
}
 
say sieve(100).join(",");
```


Recursive solution:

```ruby
func sieve(Number n) { sieve(2..n) }
func sieve(Array a   { .first > .last.sqrt }) { a }
func sieve(Array a)  { [a[0], sieve(a.grep { !(_ %% a[0]) })...] }
 
say sieve(100).join(",");
```