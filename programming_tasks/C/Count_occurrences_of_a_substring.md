[1]: http://rosettacode.org/wiki/Count_occurrences_of_a_substring

# [Count occurrences of a substring][1]

*Built-in:*

```ruby
say "the three truths".count("th")
say "ababababab".count("abab")
```


*User-created function:*

```ruby
func countSubstring(s, ss) {
    var re = Regex(ss.escape, 'g')      # 'g' for global
    var counter = 0
    while (s =~ re) { ++counter }
    return counter
}
 
say countSubstring("the three truths","th")
say countSubstring("ababababab","abab")
```

#### Output:
```
3
2
```
