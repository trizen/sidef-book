[1]: http://rosettacode.org/wiki/Fractran

# [Fractran][1]

```ruby
var str ="17/91, 78/85, 19/51, 23/38, 29/33, 77/29, 95/23, 77/19, 1/17, 11/13, 13/11, 15/14, 15/2, 55/1"
const FractalProgram = str.split(',').map{.num}      #=> array of rationals

func runner(n, callback) {
    var num = 2
    n.times {
        callback(num *= FractalProgram.find { |f| f * num -> is_int })
    }
}

func prime_generator(n, callback) {
    var x = 0;
    runner(Inf, { |num|
        var l = num.log2
        if (l.floor == l) {
            callback(l.int)
            ++x == n && return nil
        }
    })
}

STDOUT.autoflush(true)

runner(20, {|n| print (n, ' ') })
print "\n"

prime_generator(20, {|n| print (n, ' ') })
print "\n"
```

#### Output:
```
15 825 725 1925 2275 425 390 330 290 770 910 170 156 132 116 308 364 68 4 30
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71
```
