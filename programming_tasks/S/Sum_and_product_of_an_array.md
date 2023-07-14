[1]: https://rosettacode.org/wiki/Sum_and_product_of_an_array

# [Sum and product of an array][1]

Using built-in methods:

```ruby
var ary = [1, 2, 3, 4, 5]
say ary.sum                  # => 15
say ary.prod                 # => 120
```


Alternatively, using hyper-operators:

```ruby
var ary = [1, 2, 3, 4, 5]
say ary«+»                   # => 15
say ary«*»                   # => 120
```
