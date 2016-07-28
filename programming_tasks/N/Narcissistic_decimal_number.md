[1]: http://rosettacode.org/wiki/Narcissistic_decimal_number

# [Narcissistic decimal number][1]

```ruby
func is_narcissistic(n) {
    n.digits »**» n.len -> sum(0) == n
}
 
var count = 0
Inf.itimes { |i|
    if (is_narcissistic(i)) {
        say "#{++count}\t#{i}"
        break if (count == 25)
    }
}
```

#### Output:
```
1       0
2       1
3       2
4       3
5       4
6       5
7       6
8       7
9       8
10      9
11      153
12      370
13      371
14      407
15      1634
16      8208
17      9474
18      54748
19      92727
20      93084
21      548834
22      1741725
23      4210818
24      9800817
25      9926315
```
