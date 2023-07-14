[1]: https://rosettacode.org/wiki/Loop_over_multiple_arrays_simultaneously

# [Loop over multiple arrays simultaneously][1]

The simplest way is by using the `Array.zip()` method:

```ruby
[%w(a b c),%w(A B C),%w(1 2 3)].zip { |i,j,k|
    say (i, j, k)
}
```

#### Output:
```
aA1
bB2
cC3
```
