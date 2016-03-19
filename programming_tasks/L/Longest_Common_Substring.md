[1]: http://rosettacode.org/wiki/Longest_Common_Substring

# [Longest Common Substring][1]

```ruby
func createSubstrings(String word) -> Array {
  gather {
    for start in (^word.len) {
      for howmany in (1 ..^ word.len-start) {
        take(word.substr(start, howmany))
      }
    }
  }
}

func findLongestCommon(String first, String second) -> String {
    createSubstrings(first) & createSubstrings(second) -> max_by { .len }
}

say findLongestCommon("thisisatest", "testing123testing")
```

#### Output:
```
test
```
