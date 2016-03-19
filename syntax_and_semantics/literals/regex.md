# Regex

A Regex object represents a regular expression, which is fully Perl5 compatible.

```ruby
/^my?\s*re(g|[ex])\z/i
```

Alternatively, one can write:

```ruby
Regex('^my?\s*re(g|[ex])\z', 'i')
```
