[1]: https://rosettacode.org/wiki/Department_numbers

# [Department numbers][1]

```ruby
@(1..7)->combinations(3, {|*a|
    a.sum == 12 || next
    a.permutations {|*b|
        b[0].is_even || next
        say (%w(police fire sanitation) ~Z b -> join(" "))
    }
})
```

#### Output:
```
["police", 4] ["fire", 1] ["sanitation", 7]
["police", 4] ["fire", 7] ["sanitation", 1]
["police", 6] ["fire", 1] ["sanitation", 5]
["police", 6] ["fire", 5] ["sanitation", 1]
["police", 2] ["fire", 3] ["sanitation", 7]
["police", 2] ["fire", 7] ["sanitation", 3]
["police", 2] ["fire", 4] ["sanitation", 6]
["police", 2] ["fire", 6] ["sanitation", 4]
["police", 4] ["fire", 2] ["sanitation", 6]
["police", 4] ["fire", 6] ["sanitation", 2]
["police", 6] ["fire", 2] ["sanitation", 4]
["police", 6] ["fire", 4] ["sanitation", 2]
["police", 4] ["fire", 3] ["sanitation", 5]
["police", 4] ["fire", 5] ["sanitation", 3]
```
