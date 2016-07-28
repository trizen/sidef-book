[1]: http://rosettacode.org/wiki/Sorting_algorithms/Cocktail_sort

# [Sorting algorithms/Cocktail sort][1]

```ruby
func cocktailsort(a) {
    var swapped = false;
    func cmpsw(i) {
        if (a[i] > a[i+1]) {
            a[i, i+1] = a[i+1, i];
            swapped = true;
        }
    }
    var max = a.end;
    do {
        { |i| cmpsw(i-1) } * max;
        swapped.not! && break;
        { |i| cmpsw(max-i) } * max;
    } while (swapped);
    return a;
}
```


Test:

```ruby
var numbers = [7,6,5,9,8,4,3,1,2,0];
say cocktailsort(numbers);

var strs = ["John", "Kate", "Zerg", "Alice", "Joe", "Jane"];
say cocktailsort(strs);
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
['Alice', 'Jane', 'Joe', 'John', 'Kate', 'Zerg']
```
