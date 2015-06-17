[1]: http://rosettacode.org/wiki/Knuth_shuffle

# [Knuth shuffle][1]

```ruby
func shuffle (a) {
 
    { |n|
        var k = (n + 1 -> rand.int);
        k == n || (a[k, n] = a[n, k]);
    } * a.offset;
 
    return a;
}
```