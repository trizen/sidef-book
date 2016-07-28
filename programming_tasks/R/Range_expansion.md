[1]: http://rosettacode.org/wiki/Range_expansion

# [Range expansion][1]

```ruby
func rangex(str) {
    str.split(',').map { |r|
        var m = r.match(/^
            (?(DEFINE) (?<int>[+-]?[0-9]+) )
            (?<from>(?&int))-(?<to>(?&int))
        $/x)
        m ? do {var c = m.ncap; @(Num(c{:from}) .. Num(c{:to}))}
          : Num(r)
    }
}

say rangex('-6,-3--1,3-5,7-11,14,15,17-20').flatten.join(',')
```

#### Output:
```
-6,-3,-2,-1,3,4,5,7,8,9,10,11,14,15,17,18,19,20
```
