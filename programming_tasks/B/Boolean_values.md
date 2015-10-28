[1]: http://rosettacode.org/wiki/Boolean_values

# [Boolean values][1]

Sidef defines the _true_ and _false_ boolean values, which are part of the _Bool_ type.

```ruby
var t = true;
var f = false;
```


In conditional expressions, anything that evaluates to zero or nothing is considered _false_, including empty arrays and empty hashes.

```ruby
if (0 || "0" || false || nil || "" || [] || :()) {
    say "true"
} else {
    say "false";
}
```

#### Output:
```
false
```