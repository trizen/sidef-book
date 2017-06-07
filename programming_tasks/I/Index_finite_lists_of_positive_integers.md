[1]: https://rosettacode.org/wiki/Index_finite_lists_of_positive_integers

# [Index finite lists of positive integers][1]

```ruby
func rank(Array arr) {
    Number(arr.join('a'), 11)
}
 
func unrank(Number n) {
    n.base(11).split('a').map { Num(_) }
}
 
var l = [1, 2, 3, 10, 100, 987654321]
say l
var n = rank(l)
say n
var l = unrank(n)
say l
```

#### Output:
```
[1, 2, 3, 10, 100, 987654321]
14307647611639042485573
[1, 2, 3, 10, 100, 987654321]
```


**Bijection:**

```ruby
func unrank(Number n) {
    n == 1 ? [0]
           : n.base(2).substr(1).split('0', -1).map{.len}
}
 
func rank(Array x) {
    x.is_empty ? 0
               : Number('1' + x.map { '1' * _ }.join('0'), 2)
}
 
for x in (0..10) {
    printf("%3d : %-18s: %d\n", x, unrank(x), rank(unrank(x)))
}
 
say ''
var x = [1, 2, 3, 5, 8]
say "#{x} => #{rank(x)} => #{unrank(rank(x))}"
```

#### Output:
```
  0 : []                : 0
  1 : [0]               : 1
  2 : [0, 0]            : 2
  3 : [1]               : 3
  4 : [0, 0, 0]         : 4
  5 : [0, 1]            : 5
  6 : [1, 0]            : 6
  7 : [2]               : 7
  8 : [0, 0, 0, 0]      : 8
  9 : [0, 0, 1]         : 9
 10 : [0, 1, 0]         : 10

[1, 2, 3, 5, 8] => 14401279 => [1, 2, 3, 5, 8]
```