[1]: https://rosettacode.org/wiki/Cartesian_product_of_two_or_more_lists

# [Cartesian product of two or more lists][1]

In Sidef, the Cartesian product of an arbitrary number of arrays is built-in as *Array.cartesian()*:

```ruby
cartesian([[1,2], [3,4], [5,6]]).say
cartesian([[1,2], [3,4], [5,6]], {|*arr| say arr })
```


Alternatively, a simple recursive implementation:

```ruby
func cartesian_product(*arr) {
 
    var c = []
    var r = []
 
    func {
        if (c.len < arr.len) {
            for item in (arr[c.len]) {
                c.push(item)
                __FUNC__()
                c.pop
            }
        }
        else {
            r.push([c...])
        }
    }()
 
    return r
}
```


Completing the task:

```ruby
say cartesian_product([1,2], [3,4])
say cartesian_product([3,4], [1,2])
```

#### Output:
```
[[1, 3], [1, 4], [2, 3], [2, 4]]
[[3, 1], [3, 2], [4, 1], [4, 2]]
```


The product of an empty list with any other list is empty:

```ruby
say cartesian_product([1,2], [])
say cartesian_product([], [1,2])
```

#### Output:
```
[]
[]
```


Extra credit:

```ruby
cartesian_product([1776, 1789], [7, 12], [4, 14, 23], [0, 1]).each{ .say }
```

#### Output:
```
[1776, 7, 4, 0]
[1776, 7, 4, 1]
[1776, 7, 14, 0]
[1776, 7, 14, 1]
[1776, 7, 23, 0]
[1776, 7, 23, 1]
[1776, 12, 4, 0]
[1776, 12, 4, 1]
[1776, 12, 14, 0]
[1776, 12, 14, 1]
[1776, 12, 23, 0]
[1776, 12, 23, 1]
[1789, 7, 4, 0]
[1789, 7, 4, 1]
[1789, 7, 14, 0]
[1789, 7, 14, 1]
[1789, 7, 23, 0]
[1789, 7, 23, 1]
[1789, 12, 4, 0]
[1789, 12, 4, 1]
[1789, 12, 14, 0]
[1789, 12, 14, 1]
[1789, 12, 23, 0]
[1789, 12, 23, 1]
```
```ruby
say cartesian_product([1, 2, 3], [30], [500, 100])
say cartesian_product([1, 2, 3], [], [500, 100])
```

#### Output:
```
[[1, 30, 500], [1, 30, 100], [2, 30, 500], [2, 30, 100], [3, 30, 500], [3, 30, 100]]
[]
```