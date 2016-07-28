[1]: http://rosettacode.org/wiki/Longest_increasing_subsequence

# [Longest increasing subsequence][1]

Dynamic programming:

```ruby
func lis(a) {
    var l = a.len.of { [] }
    l[0] << a[0]
    for i in (1..a.end) {
        for j in ^i {
            if ((a[j] < a[i]) && (l[i].len < l[j].len+1)) {
                l[i] = [l[j]...]
            }
        }
        l[i] << a[i]
    }
    l.max_by { .len }
}

say lis(%i<3 2 6 4 5 1>)
say lis(%i<0 8 4 12 2 10 6 14 1 9 5 13 3 11 7 15>)
```


Patience sorting:

```ruby
func lis(deck) {
    var pileTops = []
    deck.each { |x|
        var low = 0;
        var high = pileTops.end
        while (low <= high) {
            var mid = ((low + high) // 2)
            if (pileTops[mid]{:val} >= x) {
                high = mid-1
            } else {
                low = mid+1
            }
        }
        var i = low
        var node = Hash(val => x)
        node{:back} = pileTops[i-1] if (i != 0)
        pileTops[i] = node
    }
    var result = []
    for (var node = pileTops[-1]; node; node = node{:back}) {
        result << node{:val}
    }
    result.reverse
}
 
say lis(%i<3 2 6 4 5 1>)
say lis(%i<0 8 4 12 2 10 6 14 1 9 5 13 3 11 7 15>)
```

#### Output:
```
[2, 4, 5]
[0, 2, 6, 9, 11, 15]
```
