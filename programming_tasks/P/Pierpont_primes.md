[1]: https://rosettacode.org/wiki/Pierpont_primes

# [Pierpont primes][1]

```ruby
func smooth_generator(primes) {
    var s = primes.len.of { [1] }
    {
        var n = s.map { .first }.min
        { |i|
            s[i].shift if (s[i][0] == n)
            s[i] << (n * primes[i])
        } * primes.len
        n
    }
}
 
func pierpont_primes(n, k = 1) {
    var g = smooth_generator([2,3])
    1..Inf -> lazy.map { g.run + k }.grep { .is_prime }.first(n)
}
 
say "First 50 Pierpont primes of the 1st kind: "
say pierpont_primes(50, +1).join(' ')
 
say "\nFirst 50 Pierpont primes of the 2nd kind: "
say pierpont_primes(50, -1).join(' ')
 
for n in (250, 500, 1000) {
    var p = pierpont_primes(n, +1).last
    var q = pierpont_primes(n, -1).last
    say "\n#{n}th Pierpont prime of the 1st kind: #{p}"
    say "#{n}th Pierpont prime of the 2nd kind: #{q}"
}
```

#### Output:
```
First 50 Pierpont primes of the 1st kind: 
2 3 5 7 13 17 19 37 73 97 109 163 193 257 433 487 577 769 1153 1297 1459 2593 2917 3457 3889 10369 12289 17497 18433 39367 52489 65537 139969 147457 209953 331777 472393 629857 746497 786433 839809 995329 1179649 1492993 1769473 1990657 2654209 5038849 5308417 8503057

First 50 Pierpont primes of the 2nd kind: 
2 3 5 7 11 17 23 31 47 53 71 107 127 191 383 431 647 863 971 1151 2591 4373 6143 6911 8191 8747 13121 15551 23327 27647 62207 73727 131071 139967 165887 294911 314927 442367 472391 497663 524287 786431 995327 1062881 2519423 10616831 17915903 18874367 25509167 30233087

250th Pierpont prime of the 1st kind: 62518864539857068333550694039553
250th Pierpont prime of the 2nd kind: 4111131172000956525894875083702271

500th Pierpont prime of the 1st kind: 2228588214163334773718162801501181906563609505773852212825423873
500th Pierpont prime of the 2nd kind: 1582451786724712011220565860035647126064921139018525742951994237124607

1000th Pierpont prime of the 1st kind: 69269314716439690250482558089997110961545818230232043107188537422260188701607997086273960899938499201024414931399264696270849
1000th Pierpont prime of the 2nd kind: 1308088756227965581249669045506775407896673213729433892383353027814827286537163695213418982500477392209371001259166465228280492460735463423
```
