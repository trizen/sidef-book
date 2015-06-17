[1]: http://rosettacode.org/wiki/Optional_parameters

# [Optional parameters][1]

```ruby
func table_sort(table, ordering: '<=>', column: 0, reverse: false) {
  if (reverse) {
    table.sort {|a,b| b[column].$ordering(a[column])}
  } else {
    table.sort {|a,b| a[column].$ordering(b[column])}
  }
}
 
# Quick example:
var table = [
  ["Ottowa", "Canada"],
  ["Washington", "USA"],
  ["Mexico City", "Mexico"],
];
 
say table_sort(table, column: 1).dump;
```

#### Output:
```
[["Ottowa", "Canada"], ["Mexico City", "Mexico"], ["Washington", "USA"]]
```


You can also create and provide a custom method for sorting to _ordering_:

```ruby
class String {
    method my_sort(arg) {
           (self.len <=> arg.len)
        || (self.lc <=> arg.lc)
        || (self <=> arg)
    }
}
 
say table_sort(table, column: 1, ordering: 'my_sort').dump;
```

#### Output:
```
[["Washington", "USA"], ["Ottowa", "Canada"], ["Mexico City", "Mexico"]]
```