[1]: https://rosettacode.org/wiki/Thue-Morse

# [Thue-Morse][1]

```ruby
func recmap(repeat, seed, transform, callback) {
    func (repeat, seed) {
        callback(seed)
        repeat > 0 && __FUNC__(repeat-1, transform(seed))
    }(repeat, seed)
}
 
recmap(6, "0", {|s| s + s.tr('01', '10') }, { .say })
```

#### Output:
```
0
01
0110
01101001
0110100110010110
01101001100101101001011001101001
0110100110010110100101100110100110010110011010010110100110010110
```