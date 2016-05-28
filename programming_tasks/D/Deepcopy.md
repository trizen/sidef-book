[1]: http://rosettacode.org/wiki/Deepcopy

# [Deepcopy][1]

_Sys.copy()_ returns a deep clone of any object.

```ruby
var src = Hash(foo => 0, bar => [0,1]);
 
# Add a cyclic reference
src{:baz} = src;
 
# Make a copy
var dst = Sys.copy(src);
 
# The address of src
say Sys.refaddr(src);
say Sys.refaddr(src{:baz});
 
# The address of dst
say Sys.refaddr(dst);
say Sys.refaddr(dst{:baz});
```

#### Output:
```
15154128
15154128
25296304
25296304
```
