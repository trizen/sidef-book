[1]: https://rosettacode.org/wiki/Forward_difference

# [Forward difference][1]

```ruby
func dif(arr) {
    gather {
        for i (0 ..^ arr.end) {
            take(arr[i+1] - arr[i])
        }
    }
}
 
func difn(n, arr) {
    { arr = dif(arr) } * n
    arr
}
 
say dif([1, 23, 45, 678])       # => [22, 22, 633]
say difn(2, [1, 23, 45, 678])   # => [0, 611]
```
