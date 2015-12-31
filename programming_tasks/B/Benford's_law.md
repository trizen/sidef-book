[1]: http://rosettacode.org/wiki/Benford's_law

# [Benford's law][1]

```ruby
var (actuals, expected) = ([], []);
var fibonacci = 1000.of {|i| fib(i-1).digit(0) }

{ |i|
    var num = fibonacci.count { |j| j == i };
    actuals.append(num / 1000);
    expected.append(1 + (1/i) -> log10);
} * 9;

"%17s%17s\n".printf("Observed","Expected");
{ |i|
    "%d : %11s %%%15s %%\n".printf(
            i, "%.2f".sprintf(100 *  actuals[i - 1]),
               "%.2f".sprintf(100 * expected[i - 1]),
    );
} * 9;
```

#### Output:
```
         Observed         Expected
1 :       30.10 %          30.10 %
2 :       17.70 %          17.61 %
3 :       12.50 %          12.49 %
4 :        9.50 %           9.69 %
5 :        8.00 %           7.92 %
6 :        6.70 %           6.69 %
7 :        5.60 %           5.80 %
8 :        5.30 %           5.12 %
9 :        4.50 %           4.58 %
```
