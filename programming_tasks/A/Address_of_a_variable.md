[1]: http://rosettacode.org/wiki/Address_of_a_variable

# [Address of a variable][1]

There is no way to access the address of a variable in Sidef, but you access the address of an object.

```ruby
var n = 42;
say Sys.refaddr(n);
 
var x = n;          # "x" will point at the same object at which "n" points to
say Sys.refaddr(x);
```

#### Output:
```
26411640
26411640
```