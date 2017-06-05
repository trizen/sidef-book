[1]: https://rosettacode.org/wiki/Faulhaber's_triangle

# [Faulhaber's triangle][1]

```ruby
func faulhaber_triangle(p) {
    gather {
        for j in (p+1 ^.. 0) {
            take(binomial(p+1, j) * bernoulli(j) / (p+1))
        }
    }
}
 
#
## First 10 rows of Faulhaber's triangle:
#
for p in (0 .. 9) {
    say faulhaber_triangle(p).map{ '%6s' % .as_rat }.join
}
 
#
## Extra credit:
#
const p = 17
const n = 1000
 
say ''
say faulhaber_triangle(p).map_kv{|k,v| v * n**(k+1) }.sum
```

#### Output:
```
     1
   1/2   1/2
   1/6   1/2   1/3
     0   1/4   1/2   1/4
 -1/30     0   1/3   1/2   1/5
     0 -1/12     0  5/12   1/2   1/6
  1/42     0  -1/6     0   1/2   1/2   1/7
     0  1/12     0 -7/24     0  7/12   1/2   1/8
 -1/30     0   2/9     0 -7/15     0   2/3   1/2   1/9
     0 -3/20     0   1/2     0 -7/10     0   3/4   1/2  1/10

56056972216555580111030077961944183400198333273050000
```