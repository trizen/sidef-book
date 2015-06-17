[1]: http://rosettacode.org/wiki/Sorting_algorithms/Radix_sort

# [Sorting algorithms/Radix sort][1]

```ruby
class Array {
    method radix_sort(base=10) {
        var arr = self.copy;
        var rounds = (arr.minmax.map{.abs}.max -> log(base).floor + 1);
        0 .. rounds-1 each { |i|
            var buckets = (2*base of {[]});
            var base_i = base**i;
            arr.each { |n|
                var digit = (n/base_i % base);
                {digit += base} if (0 <= n);
                buckets[digit].append(n);
            };
            arr = buckets.flatten;
        };
        return arr;
    }
}
 
[
    [1, 3, 8, 9, 0, 0, 8, 7, 1, 6],
    [170, 45, 75, 90, 2, 24, 802, 66],
    [170, 45, 75, 90, 2, 24, -802, -66],
    [100000, -10000, 400, 23, 10000],
].each { |arr|
    say arr.radix_sort.dump;
};
```

#### Output:
```
[0, 0, 1, 1, 3, 6, 7, 8, 8, 9]
[2, 24, 45, 66, 75, 90, 170, 802]
[-802, -66, 2, 24, 45, 75, 90, 170]
[-10000, 23, 400, 10000, 100000]
```