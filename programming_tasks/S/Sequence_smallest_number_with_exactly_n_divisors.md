[1]: https://rosettacode.org/wiki/Sequence:_smallest_number_with_exactly_n_divisors

# [Sequence: smallest number with exactly n divisors][1]

```ruby
func n_divisors(n) {
    1..Inf -> first_by { .sigma0 == n }
}

say 15.of { n_divisors(_+1) }
```

#### Output:
```
[1, 2, 4, 6, 16, 12, 64, 24, 36, 48, 1024, 60, 4096, 192, 144]
```


More efficient solution:

```ruby
func n_divisors(threshold, least_solution = Inf, k = 1, max_a = Inf, solutions = 1, n = 1) {

    if (solutions == threshold) {
        return n
    }

    if (solutions > threshold) {
        return least_solution
    }

    var p = k.prime

    for a in (1 .. max_a) {
        n *= p
        break if (n > least_solution)
        least_solution = __FUNC__(threshold, least_solution, k+1, a, solutions * (a + 1), n)
    }

    return least_solution
}

say n_divisors(60)     #=> 5040
say n_divisors(1000)   #=> 810810000
```
