[1]: http://rosettacode.org/wiki/Comma_quibbling

# [Comma quibbling][1]

```ruby
func comma_quibbling(words) {
    '{' + ([words.first(-1).join(', ')]-[''] + [words.last] -> join(' and ')) + '}'
}

[<>, <ABC>, <ABC DEF>, <ABC DEF G H>].each { |w|
    say comma_quibbling(w)
}
```

#### Output:
```
{}
{ABC}
{ABC and DEF}
{ABC, DEF, G and H}
```
