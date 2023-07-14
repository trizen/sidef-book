[1]: https://rosettacode.org/wiki/Knuth's_algorithm_S

# [Knuth's algorithm S][1]

```ruby
func s_of_n_creator(n) {
    var i = 0
    var sample = []
    { |item|
        if (++i <= n) {
            sample << item;
        }
        elsif (i.rand < n) {
            sample[n.rand] = item;
        }
        sample;
    }
}
 
var items = 0..9;
var bin = [];
 
100000.times {
    var s_of_n = s_of_n_creator(3);
    var sample = []
    for item in items {
        sample = s_of_n(item);
    }
    for s in sample {
        bin[s] := 0 ++;
    }
}
 
say bin;
```

#### Output:
```
[30056, 29906, 30058, 29986, 30062, 29748, 29989, 29985, 30126, 30084]
```