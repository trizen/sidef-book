[1]: https://rosettacode.org/wiki/Averages/Mode

# [Averages/Mode][1]

```ruby
func mode(array) {
    var c = Hash()
    array.each{|i| c{i} := 0 ++}
    var max = c.values.max
    c.keys.grep{|i| c{i} == max}
}
```


*Calling the function*

```ruby
say mode([1, 3, 6, 6, 6, 6, 7, 7, 12, 12, 17]).join(' ')
say mode([1, 1, 2, 4, 4]).join(' ')
```

#### Output:
```
6
1 4
```


If you just want one mode (instead of all of them), here's a one-liner for that:

```ruby
func one_mode(arr) {
    arr.max_by{|i| arr.count(i)}
}
```
