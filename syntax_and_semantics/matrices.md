# Matrices

In Sidef, matrices can be represented with 2-dimensional arrays:

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

Starting with version 3.06, Sidef provides a set of basic matrix operations, such as addition, subtraction, multiplication, transposition, inverse, determinant and support for solving systems of linear equations. This operations are described bellow:

```ruby
A `mmul` B      # matrix multiplication
A `madd` A      # matrix addition (entrywise)
A `msub` A      # matrix subtraction (entrywise)
```

The last two methods are provided by `Array.wise_op()`, which takes two arbitrary nested arrays and an operator, folding each element (entrywise) with the provided operator.

Example:

```ruby
say ([1,2,[3,[4]]] `madd` [42,43,[44,[45]]])    #=> [43, 45, [47, [49]]]
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

The following methods require 2-dimensional arrays exclusively:

```ruby
A.transpose         # matrix transposition
A.inv               # matrix inverse
A.det               # matrix determinant
A.msolve(vector)    # solves a system of linear equations
```

Example:

```ruby
var A = [
    [2, -1,  5,  1],
    [3,  2,  2, -6],
    [1,  3,  3, -1],
    [5, -2, -3,  3],
]

say A.det                            #=> 684
say (A `msolve` [-3, -32, -47, 49])  #=> [2, -12, -4, 1]
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
