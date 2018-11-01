# Multidimensional arrays

Multidimensional arrays can be defined as:

```ruby
var A = [
          [1, 2],
          [3, 4],
          [5, 6],
          [7, 8],
        ]

var B = [
          [1, 2, 3],
          [4, 5, 6],
        ]
```

Starting with version 3.06, Sidef provides the `Array.wise_op()` method, which takes two arbitrary nested arrays and an operator, folding each element (entrywise) with the provided operator, which is also available as `a ~Wop b`:

Example:

```ruby
say ([1,2,[3,[4]]] ~W+ [42,43,[44,[45]]])       #=> [43, 45, [47, [49]]]
```

Alternatively:

```ruby
say wise_op([1,2,[3,[4]]], '+', [42,43,[44,[45]]])   #=> [43, 45, [47, [49]]]
```

Scalar operations:

```ruby
A `scalar_add` 42   # scalar addition       (aliased as `sadd`)
A `scalar_sub` 42   # scalar subtraction    (aliased as `ssub`)
A `scalar_mul` 42   # scalar multiplication (aliased as `smul`)
A `scalar_div` 42   # scalar division       (aliased as `sdiv`)
```

This methods are provided by `Array.scalar_op()`, which, just like `Array.wise_op()`, also supports arbitrary nested arrays.

Examples:

```ruby
say ([1,2,[3,[4]]] `sadd` 42)   #=> [43, 44, [45,  [46]]]
say ([1,2,[3,[4]]] `smul` 42)   #=> [42, 84, [126, [168]]]
```

...which is equivalent with:

```ruby
say scalar_op([1,2,[3,[4]]], '+', 42)  #=> [43, 44, [45,  [46]]]
say scalar_op([1,2,[3,[4]]], '*', 42)  #=> [42, 84, [126, [168]]]
```

...and also equivalent with:

```ruby
say ([1,2,[3,[4]]] ~S+ 42)   #=> [43, 44, [45,  [46]]]
say ([1,2,[3,[4]]] ~S* 42)   #=> [42, 84, [126, [168]]]
```

## Matrix iteration

The extended `for-in` loop, introduced in Sidef 2.23, provides built-in support for matrix iteration, which is also useful in combination with the cross or zip metaoperators.

```ruby
for a,b in ([1,2] ~X [3,4]) {
    say "#{a} #{b}"
}
```

Output:

```text
1 3
1 4
2 3
2 4
```
