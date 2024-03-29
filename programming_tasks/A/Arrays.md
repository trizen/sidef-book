[1]: https://rosettacode.org/wiki/Arrays

# [Arrays][1]

```ruby
# create an empty array
var arr = []

# push objects into the array
arr << "a"            #: ['a']
arr.append(1,2,3)     #: ['a', 1, 2, 3]

# change an element inside the array
arr[2] = "b"          #: ['a', 1, 'b', 3]

# set the value at a specific index in the array (with autovivification)
arr[5] = "end"        #: ['a', 1, 'b', 3, nil, 'end']

# resize the array
arr.resize_to(-1)     #: []

# slice assignment
arr[0..2] = ('a'..'c')...       #: ['a', 'b', 'c']

# indices as arrays
var indices = [0, -1]
arr[indices] = ("foo", "baz")   #: ['foo', 'b', 'baz']

# retrieve multiple elements
var *elems = arr[0, -1]
say elems                #=> ['foo', 'baz']

# retrieve an element
say arr[-1]              #=> 'baz'
```
