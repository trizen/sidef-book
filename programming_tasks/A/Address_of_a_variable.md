[1]: https://rosettacode.org/wiki/Address_of_a_variable

# [Address of a variable][1]

```ruby
var n = 42;
say Sys.refaddr(\n);        # prints the address of the variable
say Sys.refaddr(n);         # prints the address of the object at which the variable points to
```

#### Output:
```
42823224
37867184
```
