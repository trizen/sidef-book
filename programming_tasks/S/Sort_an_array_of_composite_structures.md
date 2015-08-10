[1]: http://rosettacode.org/wiki/Sort_an_array_of_composite_structures

# [Sort an array of composite structures][1]

```ruby
# Declare an array of pairs
var people = [['joe', 120], ['foo', 31], ['bar', 51]];
 
# Sort the array in-place by name
people.sort! {|a,b| a[0] <=> b[0] };
 
# Display the sorted array
say people;
```

#### Output:
```
[["bar", 51], ["foo", 31], ["joe", 120]]
```