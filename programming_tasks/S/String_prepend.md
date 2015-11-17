[1]: http://rosettacode.org/wiki/String_prepend

# [String prepend][1]

```ruby
var str = 'llo!';
str.sub!(/^/, 'He');
say str;
```

or

```ruby
var str = 'llo!';
str.prepend!('He');
say str;
```

#### Output:
```
Hello!
```
