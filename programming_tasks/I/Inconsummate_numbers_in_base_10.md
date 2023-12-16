[1]: https://rosettacode.org/wiki/Inconsummate_numbers_in_base_10

# [Inconsummate numbers in base 10][1]

```ruby
var gen_inconsummate = Enumerator({|callback|

    for n in (1..Inf) {
        for k in (1..Inf) {

            if (9*k*n < 10**(k-1)) {
                callback(n)
                break
            }

            var check = false
            10.combinations_with_repetition(k, {|*d|
                var s = d.sum || next
                if (Str(s*n).sort == d.join) {
                    check = true
                    break
                }
            })
            check || next
            break
        }
    }
})

with (50) {|n|
    say "First #{n} inconsummate numbers (in base 10):"
    gen_inconsummate.first(n).each_slice(10, {|*s|
        say s.map{ '%3s' % _ }.join(' ')
    })
}
```

#### Output:
```
First 50 inconsummate numbers (in base 10):
 62  63  65  75  84  95 161 173 195 216
261 266 272 276 326 371 372 377 381 383
386 387 395 411 416 422 426 431 432 438
441 443 461 466 471 476 482 483 486 488
491 492 493 494 497 498 516 521 522 527
```
