[1]: https://rosettacode.org/wiki/Mertens_function

# [Mertens function][1]

Built-in:

```ruby
say mertens(123456789)   #=> 1170
say mertens(1234567890)  #=> 9163
```


Algorithm for computing M(n) in sublinear time:

```ruby
func mertens(n) is cached {
 
    var lookup_size    = (2 * n.iroot(3)**2)
    var mertens_lookup = [0]
 
    for k in (1..lookup_size) {
        mertens_lookup[k] = (mertens_lookup[k-1] + k.moebius)
    }
 
    static cache = Hash()
 
    func (n) {
 
        if (n <= lookup_size) {
            return mertens_lookup[n]
        }
 
        if (cache.has(n)) {
            return cache{n}
        }
 
        var M = 1
        var s = n.isqrt
 
        for k in (2 .. floor(n/(s+1))) {
            M -= __FUNC__(floor(n/k))
        }
 
        for k in (1..s) {
            M -= (mertens_lookup[k] * (floor(n/k) - floor(n/(k+1))))
        }
 
        cache{n} = M
    }(n)
}
```


Task:

```ruby
with (200) {|n|
    say "Mertens function in the range 1..#{n}:"
    (1..n).map { mertens(_) }.slices(20).each {|line|
        say line.map{ "%2s" % _ }.join(' ')
    }
}
 
with (1000) {|n|
    say "\nIn the range 1..#{n}, there are:"
    say (1..n->count_by { mertens(_)==0 }, " zeros")
    say (1..n->count_by { mertens(_)==0 && mertens(_-1)!=0 }, " zero crossings")
}
```

#### Output:
```
Mertens function in the range 1..200:
 1  0 -1 -1 -2 -1 -2 -2 -2 -1 -2 -2 -3 -2 -1 -1 -2 -2 -3 -3
-2 -1 -2 -2 -2 -1 -1 -1 -2 -3 -4 -4 -3 -2 -1 -1 -2 -1  0  0
-1 -2 -3 -3 -3 -2 -3 -3 -3 -3 -2 -2 -3 -3 -2 -2 -1  0 -1 -1
-2 -1 -1 -1  0 -1 -2 -2 -1 -2 -3 -3 -4 -3 -3 -3 -2 -3 -4 -4
-4 -3 -4 -4 -3 -2 -1 -1 -2 -2 -1 -1  0  1  2  2  1  1  1  1
 0 -1 -2 -2 -3 -2 -3 -3 -4 -5 -4 -4 -5 -6 -5 -5 -5 -4 -3 -3
-3 -2 -1 -1 -1 -1 -2 -2 -1 -2 -3 -3 -2 -1 -1 -1 -2 -3 -4 -4
-3 -2 -1 -1  0  1  1  1  0  0 -1 -1 -1 -2 -1 -1 -2 -1  0  0
 1  1  0  0 -1  0 -1 -1 -1 -2 -2 -2 -3 -4 -4 -4 -3 -2 -3 -3
-4 -5 -4 -4 -3 -4 -3 -3 -3 -4 -5 -5 -6 -5 -6 -6 -7 -7 -8 -8

In the range 1..1000, there are:
92 zeros
59 zero crossings
```
