[1]: https://rosettacode.org/wiki/Anonymous_recursion

# [Anonymous recursion][1]

\_\_FUNC\_\_ refers to the current function.

```ruby
func fib(n) {
    return NaN if (n < 0)

    func (n) {
        n < 2 ? n
              : (__FUNC__(n-1) + __FUNC__(n-2))
    }(n)
}
```


\_\_BLOCK\_\_ refers to the current block.

```ruby
func fib(n) {
    return NaN if (n < 0)

    {|n|
        n < 2 ? n
              : (__BLOCK__(n-1) + __BLOCK__(n-2))
    }(n)
}
```
