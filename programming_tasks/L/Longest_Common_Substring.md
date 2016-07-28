[1]: http://rosettacode.org/wiki/Longest_Common_Substring

# [Longest Common Substring][1]

```ruby
func createSubstrings(String word) -> Array {
  gather {
    for i,j in @(0 .. word.len).combinations(2) {
        take(word.substr(i, j-i))
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
