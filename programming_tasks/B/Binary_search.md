[1]: http://rosettacode.org/wiki/Binary_search

# [Binary search][1]

Iterative

```ruby
func binary_search(a, i) {
 
    var l = 0;
    var h = a.offset;
 
    while (l <= h) {
        var mid = (h+l / 2 -> int);
        a[mid] > i && (h = mid-1; next);
        a[mid] < i && (l = mid+1; next);
        return mid;
    }
 
    return -1;
}
```

Recursive

```ruby
func binary_search(arr, value, low=0, high=arr.end) {
    high < low && return -1;
    var middle = (high+low / 2 -> int);
 
    if (value < arr[middle]) {
        return binary_search(arr, value, low, middle-1);
    }
    elsif (value > arr[middle]) {
        return binary_search(arr, value, middle+1, high);
    }
 
    return middle;
}
```

Usage example:

```ruby
say binary_search([34, 42, 55, 778], 55);       #=> 2
```
