[1]: http://rosettacode.org/wiki/Longest_Common_Substring

# [Longest Common Substring][1]

```ruby
func createSubstrings(String word) -> Array {
   var length = word.len
   var substrings = []
   length.range.each { |start|
      1.to(length - start).each { |howmany|
         substrings << word.substr(start, howmany)
      }
   }
   return substrings
}
 
func findLongestCommon(String first, String second) -> String {
   var substringsFirst = createSubstrings(first)
   var substringsSecond = createSubstrings(second)
   var common = (substringsFirst & substringsSecond)
   common.max_by { .len }
}
 
say findLongestCommon("thisisatest", "testing123testing")
```

#### Output:
```
test
```