[1]: http://rosettacode.org/wiki/Binary_search

# [Binary search][1]

*Iterative*

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


*Recursive*

```ruby
func binary_search(array, value, low, high) {
    high < low && return -1;
    var middle = (high+low / 2 -> int);
 
    if (value < array[middle]) {
        return binary_search(array, value, low, middle-1);
    }
    elsif (value > array[middle]) {
        return binary_search(array, value, middle+1, high);
    }
 
    return middle;
}
```