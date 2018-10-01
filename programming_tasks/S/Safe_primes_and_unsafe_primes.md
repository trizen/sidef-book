[1]: https://rosettacode.org/wiki/Safe_primes_and_unsafe_primes

# [Safe primes and unsafe primes][1]

```ruby
func is_safeprime(p) {
    is_prime(p) && is_prime((p-1)/2)
}
 
func is_unsafeprime(p) {
    is_prime(p) && !is_prime((p-1)/2)
}
 
func safeprime_count(from, to) {
    from..to -> count_by(is_safeprime)
}
 
func unsafeprime_count(from, to) {
    from..to -> count_by(is_unsafeprime)
}
 
say "First 35 safe-primes:"
say (1..Inf -> lazy.grep(is_safeprime).first(35).join(' '))
say ''
say "First 40 unsafe-primes:"
say (1..Inf -> lazy.grep(is_unsafeprime).first(40).join(' '))
say ''
say "There are #{safeprime_count(1, 1e6)} safe-primes bellow 10^6"
say "There are #{unsafeprime_count(1, 1e6)} unsafe-primes bellow 10^6"
say ''
say "There are #{safeprime_count(1, 1e7)} safe-primes bellow 10^7"
say "There are #{unsafeprime_count(1, 1e7)} unsafe-primes bellow 10^7"
```

#### Output:
```
First 35 safe-primes:
5 7 11 23 47 59 83 107 167 179 227 263 347 359 383 467 479 503 563 587 719 839 863 887 983 1019 1187 1283 1307 1319 1367 1439 1487 1523 1619

First 40 unsafe-primes:
2 3 13 17 19 29 31 37 41 43 53 61 67 71 73 79 89 97 101 103 109 113 127 131 137 139 149 151 157 163 173 181 191 193 197 199 211 223 229 233

There are 4324 safe-primes bellow 10^6
There are 74174 unsafe-primes bellow 10^6

There are 30657 safe-primes bellow 10^7
There are 633922 unsafe-primes bellow 10^7
```