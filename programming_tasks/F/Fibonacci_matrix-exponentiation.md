[1]: https://rosettacode.org/wiki/Fibonacci_matrix-exponentiation

# [Fibonacci matrix-exponentiation][1]

Computing the n-th Fibonacci number, using matrix-exponentiation (this function is also built-in):

```ruby
func fibonacci(n) {
    ([[1,1],[1,0]]**n)[0][1]
}
 
say 15.of(fibonacci)    #=> [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377]
```


First and last 20 digits of the n-th Fibonacci number:

```ruby
for n in (16, 32) {
 
    var f = fibonacci(2**n)
 
    with (20) {|k|
        var a = (f // 10**(f.ilog10 - k + 1))
        var b = (f % 10**k)
        say "F(2^#{n}) = #{a} ... #{b}"
    }
}
```

#### Output:
```
F(2^16) = 73199214460290552832 ... 97270190955307463227
F(2^32) = 61999319689381859818 ... 39623735538208076347
```


More efficient approach, using Binet's formula for computing the first k digits, combined with the built-in method **fibmod(n,m)** for computing the last k digits:

```ruby
func binet_approx(n) {
    const PHI =  (1.25.sqrt + 0.5)
    const IHP = -(1.25.sqrt - 0.5)
    (log(PHI)*n - log(PHI-IHP))
}
 
func nth_fib_first_k_digits(n,k) {
    var f = binet_approx(n)
    floor(exp(f - log(10)*(floor(f / log(10) + 1))) * 10**k)
}
 
func nth_fib_last_k_digits(n,k) {
    fibmod(n, 10**k)
}
 
for n in (16, 32, 64) {
    var first20 = nth_fib_first_k_digits(2**n, 20)
    var last20  = nth_fib_last_k_digits(2**n, 20)
    say "F(2^#{n}) = #{first20} ... #{last20}"
}
```

#### Output:
```
F(2^16) = 73199214460290552832 ... 97270190955307463227
F(2^32) = 61999319689381859818 ... 39623735538208076347
F(2^64) = 11175807536929528424 ... 17529800348089840187
```
