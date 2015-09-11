[1]: http://rosettacode.org/wiki/Zeckendorf_number_representation

# [Zeckendorf number representation][1]

```ruby
func fib(n) {
    static f = [];
    n < 2 ? 1
          : (f[n] \\= (fib(n-1) + fib(n-2)));
}
 
func zeckendorf(n) {
    n == 0 && return '0';
    var i = 1;
    while (fib(i) <= n) { i++ };
    gather {
        while (--i > 0) {
            var f = fib(i);
            f > n ? (take '0')
                  : (take '1'; n -= f);
        }
    }.join('');
}
 
range(0, 20).each { |n|
    printf("%4d: %8s\n", n, zeckendorf(n))
}
```

#### Output:
```
   0:        0
   1:        1
   2:       10
   3:      100
   4:      101
   5:     1000
   6:     1001
   7:     1010
   8:    10000
   9:    10001
  10:    10010
  11:    10100
  12:    10101
  13:   100000
  14:   100001
  15:   100010
  16:   100100
  17:   100101
  18:   101000
  19:   101001
  20:   101010
```