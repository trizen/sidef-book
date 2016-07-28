[1]: http://rosettacode.org/wiki/Knuth_shuffle

# [Knuth shuffle][1]

```ruby
func shuffle(a) {

    { |n|
        var k = (n+1 -> irand);
        k == n || (a[k, n] = a[n, k]);
    } * a.end;

    return a;
}

say shuffle(@(1..10));
```

#### Output:
```
[7, 4, 3, 8, 9, 6, 10, 2, 1, 5]
```
