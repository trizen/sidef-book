[1]: https://rosettacode.org/wiki/Binary_search

# [Binary search][1]

Iterative

```ruby
func binary_search(a, i) {
 
    var l = 0
    var h = a.end
 
    while (l <= h) {
        var mid = (h+l / 2 -> int)
        a[mid] > i && (h = mid-1; next)
        a[mid] < i && (l = mid+1; next)
        return mid
    }
 
    return -1
}
```

Recursive

```ruby
func binary_search(arr, value, low=0, high=arr.end) {
    high < low && return -1
    var middle = ((high+low) // 2)

    given (arr[middle]) { |item|
        case (value < item) {
            binary_search(arr, value, low, middle-1)
        }
        case (value > item) {
            binary_search(arr, value, middle+1, high)
        }
        case (value == item) {
            middle
        }
    }
}
```

Usage example:

```ruby
say binary_search([34, 42, 55, 778], 55)       #=> 2
```
