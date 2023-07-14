[1]: https://rosettacode.org/wiki/Deepcopy

# [Deepcopy][1]

_Object.dclone()_ returns a deep clone of any mutable object.

```ruby
var src = Hash(foo => 0, bar => [0,1])

# Add a cyclic reference
src{:baz} = src

# Make a deep clone
var dst = src.dclone

# The address of src
say src.object_id
say src{:baz}.object_id

# The address of dst
say dst.object_id
say dst{:baz}.object_id
```

#### Output:
```
15154128
15154128
25296304
25296304
```
