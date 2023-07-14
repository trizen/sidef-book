[1]: https://rosettacode.org/wiki/Named_parameters

# [Named parameters][1]

```ruby
func example(foo: 0, bar: 1, grill: "pork chops") {
    say "foo is #{foo}, bar is #{bar}, and grill is #{grill}";
}
 
# Note that :foo is omitted and :grill precedes :bar
example(grill: "lamb kebab", bar: 3.14);
```

#### Output:
```
foo is 0, bar is 3.14, and grill is lamb kebab
```