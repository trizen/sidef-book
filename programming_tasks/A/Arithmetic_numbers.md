[1]: https://rosettacode.org/wiki/Arithmetic_numbers

# [Arithmetic numbers][1]

```ruby
func is_arithmetic(n) {
    n.tau `divides` n.sigma
}

say "The first one hundred arithmetic numbers:"
100.by(is_arithmetic).each_slice(10, {|*a|
    a.map { '%3s' % _ }.join(' ').say
})

for x in (1e3, 1e4, 1e5, 1e6) {
    var arr = x.by(is_arithmetic)
    say "\n#{x}th arithmetic number is #{arr.last}."
    say "There are #{arr.count{.is_composite}} composite arithmetic numbers <= #{arr.last}."
}
```

#### Output:
```
The first one hundred arithmetic numbers:
  1   3   5   6   7  11  13  14  15  17
 19  20  21  22  23  27  29  30  31  33
 35  37  38  39  41  42  43  44  45  46
 47  49  51  53  54  55  56  57  59  60
 61  62  65  66  67  68  69  70  71  73
 77  78  79  83  85  86  87  89  91  92
 93  94  95  96  97  99 101 102 103 105
107 109 110 111 113 114 115 116 118 119
123 125 126 127 129 131 132 133 134 135
137 138 139 140 141 142 143 145 147 149

1000th arithmetic number is 1361.
There are 782 composite arithmetic numbers <= 1361.

10000th arithmetic number is 12953.
There are 8458 composite arithmetic numbers <= 12953.

100000th arithmetic number is 125587.
There are 88219 composite arithmetic numbers <= 125587.

1000000th arithmetic number is 1228663.
There are 905043 composite arithmetic numbers <= 1228663.
```
