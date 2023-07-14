[1]: https://rosettacode.org/wiki/Entropy/Narcissist

# [Entropy/Narcissist][1]

```ruby
func entropy(s) {
    [0,
        s.chars.freq.values.map {|c|
            var f = c/s.len
            f * f.log2
        }...
    ]«-»
}
 
say entropy(File(__FILE__).open_r.slurp)
```

#### Output:
```
4.27307750866434915713432109186549
```