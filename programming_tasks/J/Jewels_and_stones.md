[1]: https://rosettacode.org/wiki/Jewels_and_stones

# [Jewels and stones][1]

```ruby
func countJewels(s, j) {
    s.chars.count { |c|
        j.contains(c)
    }
}
 
say countJewels("aAAbbbb", "aA")    #=> 3
say countJewels("ZZ", "z")          #=> 0
```
