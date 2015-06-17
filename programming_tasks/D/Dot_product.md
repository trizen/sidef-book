[1]: http://rosettacode.org/wiki/Dot_product

# [Dot product][1]

```ruby
func dot_product(vec_a is [], vec_b is []) {
    var vectors = MultiArr.new(vec_a, vec_b);
    vectors.map {|a,b| a * b}.sum;
};
say dot_product([1,3,-5], [4,-2,-1]);   # => 3
```