[1]: http://rosettacode.org/wiki/Euler's_sum_of_powers_conjecture

# [Euler's sum of powers conjecture][1]

```ruby
define range = (1 ..^ 250)

var p5 = Hash()
var sum2 = Hash()

for i in (range) {
    p5{i**5} = i
    for j in (range) {
        sum2{i**5 + j**5} = [i, j]
    }
}

var sk = sum2.keys.map{ Num(_) }.sort

for p in (p5.keys.map{ Num(_) }.sort) {

    var s = sk.first {|s|
        p > s && sum2.exists(p-s)
    } \\ next

    var t = (sum2{s} + sum2{p-s} -> map{|n| "#{n}⁵" }.join(' + '))
    say "#{t} = #{p5{p}}⁵"
    break
}
```

#### Output:
```
84⁵ + 27⁵ + 133⁵ + 110⁵ =  144⁵
```
