[1]: http://rosettacode.org/wiki/Palindrome_detection

# [Palindrome detection][1]

*Built-in*

```ruby
say "noon".is_palindrome    # true
```


*Non-recursive*

```ruby
func palindrome(s) {
    s == s.reverse
}
```


*Recursive*

```ruby
func palindrome(s) {
    if (s.len <= 1) {
        true
    }
    elsif (s.first != s.last) {
        false
    }
    else {
        __FUNC__(s.ft(1, -2))
    }
}
```
