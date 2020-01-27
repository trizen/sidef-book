[1]: https://rosettacode.org/wiki/Gapful_numbers

# [Gapful numbers][1]

Concept extended to other bases:

```ruby
func is_gapful(n, base=10) {
    n.is_div(base*floor(n / base**n.ilog(base)) + n%base)
}
 
var task = [
    "(Required) The first %s gapful numbers (>= %s)", 30, 1e2, 10,
    "(Required) The first %s gapful numbers (>= %s)", 15, 1e6, 10,
    "(Required) The first %s gapful numbers (>= %s)", 10, 1e9, 10,
    "(Extra) The first %s gapful numbers (>= %s)", 10, 987654321, 10,
    "(Extra) The first %s gapful numbers (>= %s)", 10, 987654321, 12,
]
 
task.each_slice(4, {|title, n, from, b|
    say sprintf("\n#{title} for base #{b}:", n, from.commify)
    say (from..Inf -> lazy.grep{ is_gapful(_,b) }.first(n).join(' '))
})
```

#### Output:
```
(Required) The first 30 gapful numbers (>= 100) for base 10:
100 105 108 110 120 121 130 132 135 140 143 150 154 160 165 170 176 180 187 190 192 195 198 200 220 225 231 240 242 253

(Required) The first 15 gapful numbers (>= 1,000,000) for base 10:
1000000 1000005 1000008 1000010 1000016 1000020 1000021 1000030 1000032 1000034 1000035 1000040 1000050 1000060 1000065

(Required) The first 10 gapful numbers (>= 1,000,000,000) for base 10:
1000000000 1000000001 1000000005 1000000008 1000000010 1000000016 1000000020 1000000027 1000000030 1000000032

(Extra) The first 10 gapful numbers (>= 987,654,321) for base 10:
987654330 987654334 987654336 987654388 987654420 987654485 987654510 987654513 987654592 987654600

(Extra) The first 10 gapful numbers (>= 987,654,321) for base 12:
987654325 987654330 987654336 987654360 987654368 987654384 987654388 987654390 987654393 987654395
```
