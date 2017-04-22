[1]: http://rosettacode.org/wiki/Strip_comments_from_a_string

# [Strip comments from a string][1]

```ruby
func strip_comment(s) {
    (s - %r'[#;].*').strip
}
 
[" apples, pears # and bananas",
 " apples, pears ; and bananas",
 " apples, pears "].each { |s|
    say strip_comment(s).dump;
}
```

#### Output:
```
"apples, pears"
"apples, pears"
"apples, pears"
```
