[1]: http://rosettacode.org/wiki/One-dimensional_cellular_automata

# [One-dimensional cellular automata][1]

```ruby
var seq = "_###_##_#_#_#_#__#__"
var x = ''
 
loop {
    seq.tr!('01', '_#')
    say seq
    seq.tr!('_#', '01')
    seq.gsub!(/(?<=(.))(.)(?=(.))/, {|s1,s2,s3| s1 == s3 ? (s1 ? 1-s2.to_i : 0) : s2})
    (x != seq) && (x = seq) || break
}
```

#### Output:
```
_###_##_#_#_#_#__#__
_#_#####_#_#_#______
__##___##_#_#_______
__##___###_#________
__##___#_##_________
__##____###_________
__##____#_#_________
__##_____#__________
__##________________
```
```ruby
class Automaton(rule, cells) {

    method init {
        rule = sprintf("%08b", rule).chars.map{.to_i}.flip
    }

    method next {
        var previous = cells.map{_}
        var len = previous.len
        cells[] = rule[
                previous.range.map { |i|
                    4*previous[i-1 % len] +
                    2*previous[i]         +
                      previous[i+1 % len]
                }...
            ]
    }

    method to_s {
        cells.map { _ ? '#' : ' ' }.join
    }
}

var size = 10
var auto = Automaton(
    rule: 104,
    cells: [(size/2).of(0)..., 111011010101.digits..., (size/2).of(0)...],
)

size.times {
    say "|#{auto}|"
    auto.next
}
```

#### Output:
```
|     ### ## # # #     |
|     # ##### # #      |
|      ##   ## #       |
|      ##   ###        |
|      ##   # #        |
|      ##    #         |
|      ##              |
|      ##              |
|      ##              |
|      ##              |
```
