# gather/take

The `gather/take` construct  was borrowed from Perl 6 and it's an interesting one.

```ruby
var arr = gather {
    take 1
    take 2
    take 3
}
say arr;            # prints: [1,2,3]
```

Inside a `gather{}` block, the `take` keyword is available, which accepts a list of arguments that are stored inside an automatically created array. In the end, the gather returns the array to the caller.
