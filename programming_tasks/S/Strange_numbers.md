[1]: https://rosettacode.org/wiki/Strange_numbers

# [Strange numbers][1]

```ruby
func generate_from_prefix(limit, p, base) {
 
    var seq = [p]
 
    for d in (base-1 -> primes) {
        for k in ([1, -1]) {
            var r = p[0]+(k*d)
            next if (r < 0)
            next if (r >= base)
            var t = [r, p...]
            if (t.digits2num(base) <= limit) {
                seq << __FUNC__(limit, t, base)...
            }
        }
    }
 
    return seq
}
 
func strange_numbers(limit, base = 10, digits = @(^base)) {
    digits.map {|p| generate_from_prefix(limit, [p], base)... }\
          .map {|t| t.digits2num(base) }\
          .sort.uniq
}
 
strange_numbers(500).grep { _ > 100 }.slices(10).each{
    .join(' ').say
}
```

#### Output:
```
130 131 135 136 138 141 142 146 147 149
161 163 164 168 169 181 183 185 186 202
203 205 207 241 242 246 247 249 250 252
253 257 258 270 272 274 275 279 292 294
296 297 302 303 305 307 313 314 316 318
350 352 353 357 358 361 363 364 368 369
381 383 385 386 413 414 416 418 420 424
425 427 429 461 463 464 468 469 470 472
474 475 479 492 494 496 497
```
