[1]: http://rosettacode.org/wiki/Sattolo_cycle

# [Sattolo cycle][1]

Modifies the array in-place:

```ruby
func sattolo_cycle(arr) {
    for i in (arr.len ^.. 1) {
        arr.swap(i, pick(^i))
    }
}
```
