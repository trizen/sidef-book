[1]: http://rosettacode.org/wiki/Euler's_sum_of_powers_conjecture

# [Euler's sum of powers conjecture][1]

```ruby
define MAX = 250

var p5 = Hash()
var sum2 = Hash()

MAX.times { |i|
    p5{i**5} = i
    MAX.times { |j|
        sum2{i**5 + j**5} = [i, j]
    }
}

var sk = sum2.keys.map{.to_n}.sort
p5.keys.map{.to_n}.sort.each { |p|
    sk.each { |s|
        next if (p <= s)
        if (sum2.exists(p - s)) {
            sum2{s} + sum2{p-s} -> map{|n| "#{n}⁵" }             \
                                -> join(' + ') + " =  #{p5{p}}⁵" \
                                -> say
            goto :END
        }
    }
} @:END
```

#### Output:
```
84⁵ + 27⁵ + 133⁵ + 110⁵ =  144⁵
```
