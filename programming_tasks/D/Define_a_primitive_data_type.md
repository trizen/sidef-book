[1]: http://rosettacode.org/wiki/Define_a_primitive_data_type

# [Define a primitive data type][1]

```ruby
subset Integer    < Number  { .is_int }
subset MyIntLimit < Integer { . ~~ (1 ..^ 10) }

class MyInt(value < MyIntLimit) {

    method to_s      { value.to_s }
    method get_value { value.get_value }

    method AUTOLOAD(_, name, *args) {
        var result = value.(name)(args.map {|n| Number(n) }...)
        result.kind_of(Number) ? MyInt(result.int) : result
    }
}

#
## Tests:
#
var a = MyInt(2)    # creates a new object of type `MyInt`
a += 7              # adds 7 to a
say a               # => 9
say a/2             # => 4

var b = (a - 3)     # b is of type `MyInt`
say b               # => 6

say a.as_hex.dump   # => "9" -- an hexadecimal string

a -= 7              # a=2
say (a + b)         # => 8 -- the result of (2 + 6)

a += 4              # a=6
say a+b             # error: class `MyInt` does not match MyInt(12)
```
