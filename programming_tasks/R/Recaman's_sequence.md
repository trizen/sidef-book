[1]: https://rosettacode.org/wiki/Recaman's_sequence

# [Recaman's sequence][1]

```ruby
func recamans_generator() {
 
    var term = 0
    var prev = 0
    var seen = Hash()
 
    {
        var this = (prev - term)
 
        if ((this <= 0) || seen{this}) {
            this = (prev + term)
        }
 
        prev = this
        seen{this} = true
        term++
        this
    }
}
 
with (recamans_generator()) { |r|
    say ("First 15 terms of the Recaman's sequence: ", 15.of { r.run }.join(', '))
}
 
with (recamans_generator()) {|r|
    var seen = Hash()
    Inf.times {|i|
        var n = r.run
        if (seen{n}) {
            say "First duplicate term in the series is a(#{i}) = #{n}"
            break
        }
        seen{n} = true
    }
}
 
with (recamans_generator()) {|r|
    var seen = Hash()
    Inf.times {|i|
        var n = r.run
        if ((n <= 1000) && (seen{n} := true) && (seen.len == 1001)) {
            say "Terms up to a(#{i}) are needed to generate 0 to 1000"
            break
        }
    }
}
```

#### Output:
```
First 15 terms of the Recaman's sequence: 0, 1, 3, 6, 2, 7, 13, 20, 12, 21, 11, 22, 10, 23, 9
First duplicate term in the series is a(24) = 42
Terms up to a(328002) are needed to generate 0 to 1000
```