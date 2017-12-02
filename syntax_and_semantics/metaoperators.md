# Metaoperators

In Sidef we have an interesting set of metaoperators, which provide an easier way of working with arrays and matrices.

### Unroll operator

It's a nice metaoperator borrowed from Perl 6, which unrolls two arrays and applies the operator on each two element-wise objects, creating a new array with the results. The operator can be a method or any other valid operator and must be enclosed between `» «` or `>> <<`.

```ruby
[1,2,3] »+« [4,5,6]           # [1+4, 2+5, 3+6]
%w(a b c) >>cmp<< %w(c b a)   # [-1, 0, 1]
```

Internally, the `unroll_operator` method is called, which can, also, be implemented in user-defined classes.

### Map operator

The array map operator works exactly like the `Array.map{}` method, but it's slightly more efficient and easier to write. The map operator must be enclosed between `» »` or `>> >>`.

```ruby
[1,2,3] »*» 4      # [1*4, 2*4, 3*4]
```

Internally, the `map_operator` method is called.

### Pam operator

The pam operator is kind of a reversed mapping of the array ("pam" is "map" spelled backwards), where the provided argument is used as the first operand to the operator provided. The operator must be enclosed between `« «` or `<< <<`.

```ruby
[1,2,3] «/« 10     # [10/1, 10/2, 10/3]
```

Internally, the `pam_operator` method is called.

### Reduce operator

This metaoperator reduces an array to a single element. The operator needs to be enclosed inside `« »` or `<< >>`.

```ruby
[1,2,3]«+»      # 1 + 2 + 3
[1,2,3]«/»      # 1 / 2 / 3
```

Internally, the `reduce_operator` method is called.

### Cross operator

The metaoperator `~X` or `~Xop` crosses two arrays and returns a new one.

```ruby
[1,2] ~X+ [3,4]    # [1+3, 1+4, 2+3, 2+4]
[1,2] ~X  [3,4]    # [[1,3], [1,4], [2,3], [2,4]]
```

Internally, the `cross_operator` method is called.

### Zip operator

The metaoperator `~Z` or `~Zop` zips two arrays and returns a new one.

```ruby
[1,2] ~Z+ [3,4]    # [1+3, 2+4]
[1,2] ~Z  [3,4]    # [[1,3], [2,4]]
```

Internally, the `zip_operator` method is called.

### Wise operator

Almost equivalent with the zip metaoperator, it does element-wise folding on two arbitrary nested arrays, where both arrays must have the same structure.

```ruby
[1,2]       ~W  [3,4]         # [[1,3], [2,4]]
[1,2]       ~W+ [3,4]         # [1+3, 2+4]
[[[1]],[2]] ~W+ [[[3]],[4]]   # [[[1+3]], [2+4]]
```

Internally, the `wise_operator` method is called.

### Scalar operator

The scalar operator applies a given operator to the elements of an arbitrary nested array, where the provided scalar is used as the second operand to the given operator.

```ruby
[1,2,3]       ~S  5  # [[1,5], [2,5], [3,5]]
[1,2,3]       ~S* 5  # [1*5, 2*5, 3*5]
[1,[[2,[3]]]] ~S+ 5  # [1+5, [[2+5, [3+5]]]]
```

Internally, the `scalar_operator` method is called.
