[1]: http://rosettacode.org/wiki/Polymorphic_copy

# [Polymorphic copy][1]

_Object.dclone()_ makes a deep clone of any mutable object and returns it to the caller.

```ruby
class T(value) {
    method display {
        say value;
    }
}

class S(value) < T {
    method display {
        say value;
    }
}

var obj1 = T("T");
var obj2 = S("S");
var obj3 = obj2.dclone;         # make a deep clone of obj2

obj1.value = "foo";             # change the value of obj1
obj2.value = "bar";             # change the value of obj2

obj1.display;                   # prints "foo"
obj2.display;                   # prints "bar"
obj3.display;                   # prints "S"
```
