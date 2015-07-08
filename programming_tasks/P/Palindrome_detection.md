[1]: http://rosettacode.org/wiki/Palindrome_detection

# [Palindrome detection][1]

*Non-recursive*

```ruby
func palindrome(s) {
    s == s.reverse
}
```


*Recursive*

```ruby
func r_palindrome(s) {
    if (s.len <= 1) {
        true
    }
    elsif (s.char_at(0) != s.char_at(-1)) {
        false
    }
    else {
        __FUNC__(s.substr(1, -1))
    }
}
```