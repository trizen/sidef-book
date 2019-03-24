[1]: https://rosettacode.org/wiki/Mian-Chowla_sequence

# [Mian-Chowla sequence][1]

```ruby
var (n, sums, ts, mc) = (100, Set([2]), [], [1])
var st = Time.micro_sec
for i in (1 ..^ n) {
   for j in (mc[i-1]+1 .. Inf) {
      mc[i] = j
      for k in (0 .. i) {
         var sum = mc[k]+j
         if (sums.exists(sum)) { 
            ts.clear
            break
         }
         ts << sum
      }
      if (ts.len > 0) {
         sums = (sums|Set(ts...))
         break
      }
   }
}
var et = (Time.micro_sec - st)
var s = " of the Mian-Chowla sequence are:\n"
say "The first 30 terms#{s}#{mc.ft(0, 29).join(' ')}\n"
say "Terms 91 to 100#{s}#{mc.ft(90, 99).join(' ')}\n"
say "Computation time was #{et} seconds."
```

#### Output:
```
The first 30 terms of the Mian-Chowla sequence are:
1 2 4 8 13 21 31 45 66 81 97 123 148 182 204 252 290 361 401 475 565 593 662 775 822 916 970 1016 1159 1312

Terms 91 to 100 of the Mian-Chowla sequence are:
22526 23291 23564 23881 24596 24768 25631 26037 26255 27219

Computation time was 3.9831 seconds.
```