[1]: http://rosettacode.org/wiki/Return_multiple_values

# [Return multiple values][1]

```ruby
func foo(a,b) {
    return (a+b, a*b)
}
```


Catching the returned arguments:

```ruby
var (x, y) = foo(4, 5)
say x   #=> 9
say y   #=> 20
```
