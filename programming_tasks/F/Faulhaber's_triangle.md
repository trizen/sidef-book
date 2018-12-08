[1]: https://rosettacode.org/wiki/Faulhaber's_triangle

# [Faulhaber's triangle][1]

```ruby
func faulhaber_triangle(p) {
    { binomial(p, _) * bernoulli(_) / p }.map(p ^.. 0)
}

{ |p|
    say faulhaber_triangle(p).map{ '%6s' % .as_rat }.join
} << 1..10

const p = 17
const n = 1000

say ''
say faulhaber_triangle(p+1).map_kv {|k,v| v * n**(k+1) }.sum
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

Alternative solution:

```ruby
func find_poly_degree(a) {
    var c = 0
    loop {
        ++c
        a = a.map_cons(2, {|n,k| n-k })
        return 0 if a.is_empty
        return c if a.all { .is_zero }
    }
}

func faulhaber_triangle(n) {
    var a = (0..(n+2) -> accumulate { _**n })
    var c = find_poly_degree(a)

    var A = c.of {|n|
        c.of {|k| n**k }
    }

    A.msolve(a).slice(1)
}

10.times { say faulhaber_triangle(_) }
```

#### Output:
```
[1]
[1/2, 1/2]
[1/6, 1/2, 1/3]
[0, 1/4, 1/2, 1/4]
[-1/30, 0, 1/3, 1/2, 1/5]
[0, -1/12, 0, 5/12, 1/2, 1/6]
[1/42, 0, -1/6, 0, 1/2, 1/2, 1/7]
[0, 1/12, 0, -7/24, 0, 7/12, 1/2, 1/8]
[-1/30, 0, 2/9, 0, -7/15, 0, 2/3, 1/2, 1/9]
[0, -3/20, 0, 1/2, 0, -7/10, 0, 3/4, 1/2, 1/10]
```
