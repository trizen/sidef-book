[1]: https://rosettacode.org/wiki/String_comparison

# [String comparison][1]

```ruby
var methods = %w(== != > >= < <= <=>)
for s1, s2 in [<YUP YUP>,<YUP Yup>,<bot bat>,<aaa zz>] {
    methods.each{|m| "%s %s %s\t%s\n".printf(s1, m, s2, s1.(m)(s2))}
    print "\n"
}
```
