[1]: https://rosettacode.org/wiki/Palindrome_pairs

# [Palindrome pairs][1]

```ruby
func find_palindromes(arr, callback) {
    arr.len.variations(2, {|i,j|
        var w = (arr[i]+arr[j]).fc.gsub(/\W+/)
        callback(i, j) if (w == w.flip)
    })
}
 
var t = [
    "abcd","dcba","lls","s","sssll",
    "Mr. Owl ate","or a cat I saw?",
    " my metal worm","Was it a car ",
]
 
find_palindromes(t, {|i,j|
    say "(#{i}, #{j}) = (#{t[i].dump}, #{t[j].dump})"
})
```

#### Output:
```
(0, 1) = ("abcd", "dcba")
(1, 0) = ("dcba", "abcd")
(2, 4) = ("lls", "sssll")
(3, 2) = ("s", "lls")
(5, 7) = ("Mr. Owl ate", " my metal worm")
(8, 6) = ("Was it a car ", "or a cat I saw?")
```