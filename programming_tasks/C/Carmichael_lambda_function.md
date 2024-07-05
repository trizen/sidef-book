[1]: https://rosettacode.org/wiki/Carmichael_lambda_function

# [Carmichael lambda function][1]

Built-in as **Number#carmichael\_lambda**:

```ruby
func iteratedToOne(n) {
    var k = 0
    while (n > 1) {
        n.carmichael_lambda!
        ++k
    }
    return k
}

say " n   λ   k"
say "----------"

for n in (1..25) {
    printf("%2d  %2d  %2d\n", n, n.carmichael_lambda, iteratedToOne(n))
}

say "\nIterations to 1       i     lambda(i)"
say "====================================="

var table = []

1..Inf -> each {|k|
    var n = iteratedToOne(k)
    if (!table[n]) {
        table[n] = true
        printf("%4s %18s %12s\n", n, k, k.carmichael_lambda)
        break if (n == 15)
    }
}
```

#### Output:
```
 n   λ   k
----------
 1   1   0
 2   1   1
 3   2   2
 4   2   2
 5   4   3
 6   2   2
 7   6   3
 8   2   2
 9   6   3
10   4   3
11  10   4
12   2   2
13  12   3
14   6   3
15   4   3
16   4   3
17  16   4
18   6   3
19  18   4
20   4   3
21   6   3
22  10   4
23  22   5
24   2   2
25  20   4

Iterations to 1       i     lambda(i)
=====================================
   0                  1            1
   1                  2            1
   2                  3            2
   3                  5            4
   4                 11           10
   5                 23           22
   6                 47           46
   7                283          282
   8                719          718
   9               1439         1438
  10               2879         2878
  11              34549        34548
  12             138197       138196
  13             531441       354294
  14            1594323      1062882
  15            4782969      3188646
```
