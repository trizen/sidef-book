[1]: http://rosettacode.org/wiki/Hamming_numbers

# [Hamming numbers][1]

```ruby
func ham_gen {
    var s = [[1], [1], [1]];
    var m = [2, 3, 5];
 
    func {
        var n = [s[0][0], s[1][0], s[2][0]].min;
        range(0, 2).each { |i|
            s[i].shift if (s[i][0] == n);
            s[i].append(n * m[i]);
        }
        return n
    }
}
 
var h = ham_gen();
 
var i = 20;
say i.of { h() }.join(' ');
 
range(i+1, 1691-1).each { h() }
say h();
```

#### Output:
```
1 2 3 4 5 6 8 9 10 12 15 16 18 20 24 25 27 30 32 36
2125764000
```