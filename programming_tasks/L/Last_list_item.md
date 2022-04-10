[1]: https://rosettacode.org/wiki/Last_list_item

# [Last list item][1]

### With sorting

```ruby
var k = 2
var list = [6, 81, 243, 14, 25, 49, 123, 69, 11]
 
while (list.len >= k) {
    var a = list.sort!.shift(k)
    list << a.sum
    say "#{a.map{'%3s' % _}.join(' ')} : #{list}"
}
```

#### Output:
```
  6  11 : [14, 25, 49, 69, 81, 123, 243, 17]
 14  17 : [25, 49, 69, 81, 123, 243, 31]
 25  31 : [49, 69, 81, 123, 243, 56]
 49  56 : [69, 81, 123, 243, 105]
 69  81 : [105, 123, 243, 150]
105 123 : [150, 243, 228]
150 228 : [243, 378]
243 378 : [621]
```


### Without sorting

```ruby
var k = 2
var list = [6, 81, 243, 14, 25, 49, 123, 69, 11]
 
while (list.len >= k) {
 
    var a = gather {
        k.times {
            take(var v = list.min)
            list.delete_first(v)
        }
    }
 
    list << a.sum
    say "#{a.map{'%3s' % _}.join(' ')} : #{list}"
}
```

#### Output:
```
  6  11 : [81, 243, 14, 25, 49, 123, 69, 17]
 14  17 : [81, 243, 25, 49, 123, 69, 31]
 25  31 : [81, 243, 49, 123, 69, 56]
 49  56 : [81, 243, 123, 69, 105]
 69  81 : [243, 123, 105, 150]
105 123 : [243, 150, 228]
150 228 : [243, 378]
243 378 : [621]
```
