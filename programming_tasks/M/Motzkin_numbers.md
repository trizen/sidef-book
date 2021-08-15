[1]: https://rosettacode.org/wiki/Motzkin_numbers

# [Motzkin numbers][1]

Built-in:

```ruby
say 50.of { .motzkin }
```


Motzkin's triangle (the Motzkin numbers are on the hypotenuse of the triangle):

```ruby
func motzkin_triangle(num, callback) {
    var row = []
    { |n|
        row = [0, 1, {|i| row[i+2] + row[i] + row[i+1] }.map(0 .. n-3)..., 0]
        callback(row.grep{ .> 0 })
    } << 2..(num+1)
}
 
motzkin_triangle(10, {|row|
    row.map { "%4s" % _ }.join(' ').say
})
```

#### Output:
```
   1
   1    1
   1    2    2
   1    3    5    4
   1    4    9   12    9
   1    5   14   25   30   21
   1    6   20   44   69   76   51
   1    7   27   70  133  189  196  127
   1    8   35  104  230  392  518  512  323
   1    9   44  147  369  726 1140 1422 1353  835
```


Task:

```ruby
func motzkin_numbers(N) {
 
    var (a, b, n) = (0, 1, 1)
 
    N.of {
        var M = b/n
        n += 1
        (a, b) = (b, (3*(n-1)*n*a + (2*n - 1)*n*b) / ((n+1)*(n-1)))
        M
    }
}
 
motzkin_numbers(42).each_kv {|k,v|
    say "#{'%2d' % k}: #{v}#{v.is_prime ? ' prime' : ''}"
}
```

#### Output:
```
 0: 1
 1: 1
 2: 2 prime
 3: 4
 4: 9
 5: 21
 6: 51
 7: 127 prime
 8: 323
 9: 835
10: 2188
11: 5798
12: 15511 prime
13: 41835
14: 113634
15: 310572
16: 853467
17: 2356779
18: 6536382
19: 18199284
20: 50852019
21: 142547559
22: 400763223
23: 1129760415
24: 3192727797
25: 9043402501
26: 25669818476
27: 73007772802
28: 208023278209
29: 593742784829
30: 1697385471211
31: 4859761676391
32: 13933569346707
33: 40002464776083
34: 114988706524270
35: 330931069469828
36: 953467954114363 prime
37: 2750016719520991
38: 7939655757745265
39: 22944749046030949
40: 66368199913921497
41: 192137918101841817
```
