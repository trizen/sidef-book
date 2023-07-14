[1]: https://rosettacode.org/wiki/Find_first_and_last_set_bit_of_a_long_integer

# [Find first and last set bit of a long integer][1]

Sidef has arbitrary sized integers.

```ruby
func msb(n) {
    var b = 0
    while(n >>= 1) { ++b }
    return b
}
 
func lsb(n) {
    msb(n & -n)
}
```


Test cases:

```ruby
func table (base,power) {
    var digits = length(base**power)
    printf("%#{digits}s  lsb msb\n", 'number')
    for n in (0..power) {
        var x = base**n
        printf("%#{digits}s  %2s  %3s\n", x, lsb(x), msb(x))
    }
}
 
table(42, 20)
table(1302, 20)
```