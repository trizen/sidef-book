[1]: https://rosettacode.org/wiki/Gaussian_elimination

# [Gaussian elimination][1]

Uses the `rref(A)` function from [Reduced row echelon form](https://rosettacode.org/wiki/Reduced_row_echelon_form#Sidef).

```ruby
func gauss_jordan_solve (a, b) {

    var A = gather {
        ^b -> each {|i| take(a[i] + b[i]) }
    }

    rref(A).map{ .last }
}

var a = [
    [ 1.00, 0.00, 0.00,  0.00,  0.00,   0.00 ],
    [ 1.00, 0.63, 0.39,  0.25,  0.16,   0.10 ],
    [ 1.00, 1.26, 1.58,  1.98,  2.49,   3.13 ],
    [ 1.00, 1.88, 3.55,  6.70, 12.62,  23.80 ],
    [ 1.00, 2.51, 6.32, 15.88, 39.90, 100.28 ],
    [ 1.00, 3.14, 9.87, 31.01, 97.41, 306.02 ],
]

var b = [ -0.01, 0.61, 0.91, 0.99, 0.60, 0.02 ]

var G = gauss_jordan_solve(a, b)
say G.map { "%27s" % .as_rat }.join("\n")
```

#### Output:
```
                     -1/100
  655870882787/409205648497
 -660131804286/409205648497
  509663229635/409205648497
 -200915766608/409205648497
   26909648324/409205648497
```
