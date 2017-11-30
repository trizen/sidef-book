# Variable references

Like in other programming languages, we have the capability of taking references to variables, by using the prefix backslash (`\`) operator for referencing and the prefix asterix (`*`) operator for dereferencing:

```ruby
var name = "sidef"
var ref = \name
var original = *ref
```

Variable references are useful when passing them to functions (or methods) for assigning values.

```ruby
func assign2ref (ref, value) {
    *ref = value
}

var x = 10
assign2ref(\x, 20)
say x                 # prints: 20
```

There is also the possibility of taking references to the lvalues of an array or hash:

```ruby
var a = [41, 42, 43]
var r = \a[1]           # reference of the second element

*r = 99                 # changes the value inside the array
say a                   # prints: [41, 99, 43]
```
