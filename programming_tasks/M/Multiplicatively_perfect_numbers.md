[1]: https://rosettacode.org/wiki/Multiplicatively_perfect_numbers

# [Multiplicatively perfect numbers][1]

```ruby
func multiplicatively_perfect_numbers(N) {
    [1] + semiprimes(N).grep{|n| isqrt(n**tau(n)) == n.sqr } + N.icbrt.primes.map { .cube } -> sort
}

say ("Terms <= 500: ", multiplicatively_perfect_numbers(500).join(' '), "\n")

for n in (500, 5_000, 50_000, 500_000) {
    var M = multiplicatively_perfect_numbers(n)
    say "There are #{M.len} MPNs and #{semiprime_count(n)} semiprimes <= #{n.commify}."
}
```

#### Output:
```
Terms <= 500: 1 6 8 10 14 15 21 22 26 27 33 34 35 38 39 46 51 55 57 58 62 65 69 74 77 82 85 86 87 91 93 94 95 106 111 115 118 119 122 123 125 129 133 134 141 142 143 145 146 155 158 159 161 166 177 178 183 185 187 194 201 202 203 205 206 209 213 214 215 217 218 219 221 226 235 237 247 249 253 254 259 262 265 267 274 278 287 291 295 298 299 301 302 303 305 309 314 319 321 323 326 327 329 334 335 339 341 343 346 355 358 362 365 371 377 381 382 386 391 393 394 395 398 403 407 411 413 415 417 422 427 437 445 446 447 451 453 454 458 466 469 471 473 478 481 482 485 489 493 497

There are 150 MPNs and 153 semiprimes <= 500.
There are 1354 MPNs and 1365 semiprimes <= 5,000.
There are 12074 MPNs and 12110 semiprimes <= 50,000.
There are 108223 MPNs and 108326 semiprimes <= 500,000.
```
