[1]: http://rosettacode.org/wiki/Longest_Common_Substring

# [Longest Common Substring][1]

```ruby
func createSubstrings(String word) -> Array {
   gather {
     var length = word.len;
     length.range.each { |start|
      1.to(length - start).each { |howmany|
        take word.substr(start, howmany)
      }
    }
  }
}

func findLongestCommon(String first, String second) -> String {
    (createSubstrings(first) & createSubstrings(second)) -> max_by { .len }
}

say findLongestCommon("thisisatest", "testing123testing")
```

#### Output:
```
test
```
