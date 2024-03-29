[1]: https://rosettacode.org/wiki/Elementary_cellular_automaton

# [Elementary cellular automaton][1]

```ruby
class Automaton(rule, cells) {

    method init {
        rule = sprintf("%08b", rule).chars.map{.to_i}.reverse
    }

    method next {
        var previous = cells.map{_}
        var len = previous.len
        cells[] = rule[
                    previous.range.map { |i|
                        4*previous[i-1 % len] +
                        2*previous[i]         +
                        previous[i+1 % len]
                    }
                  ]
    }

    method to_s {
        cells.map { _ ? '#' : ' ' }.join
    }
}

var size = 20
var arr = size.of(0)
arr[size/2] = 1

var auto = Automaton(90, arr)

(size/2).times {
    print "|#{auto}|\n"
    auto.next
}
```

#### Output:
```
|          #         |
|         # #        |
|        #   #       |
|       # # # #      |
|      #       #     |
|     # #     # #    |
|    #   #   #   #   |
|   # # # # # # # #  |
|  #               # |
| # #             # #|
```
