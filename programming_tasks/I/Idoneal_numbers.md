[1]: https://rosettacode.org/wiki/Idoneal_numbers

# [Idoneal numbers][1]

```ruby
func is_idoneal (n) {

    for a in (1..n) {
        for b in (a+1 .. n) {
            break if (a*b + a + b > n)
            for c in (b+1 .. n) {
                var sum = (a*b + b*c + a*c)
                return false if (n == sum)
                break if (sum > n)
            }
        }
    }

    return true
}

1..255 -> grep(is_idoneal).each_slice(10, {|*a|
    say a.map { '%4s' % _ }.join(' ')
})
```

#### Output:
```
   1    2    3    4    5    6    7    8    9   10
  12   13   15   16   18   21   22   24   25   28
  30   33   37   40   42   45   48   57   58   60
  70   72   78   85   88   93  102  105  112  120
 130  133  165  168  177  190  210  232  240  253
```
