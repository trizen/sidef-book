[1]: https://rosettacode.org/wiki/Apply_a_digital_filter_(direct_form_II_transposed)

# [Apply a digital filter (direct form II transposed)][1]

```ruby
func TDF_II_filter(signal, a, b) {
    var out = [0]*signal.len
    for i in ^signal {
        var this = 0
        for j in ^b { i-j >= 0 && (this += b[j]*signal[i-j]) }
        for j in ^a { i-j >= 0 && (this -= a[j]*   out[i-j]) }
        out[i] = this/a[0]
    }
    return out
}
 
var signal = [
    -0.917843918645,  0.141984778794, 1.20536903482,   0.190286794412,
    -0.662370894973, -1.00700480494, -0.404707073677,  0.800482325044,
     0.743500089861,  1.01090520172,  0.741527555207,  0.277841675195,
     0.400833448236, -0.2085993586,  -0.172842103641, -0.134316096293,
     0.0259303398477, 0.490105989562, 0.549391221511,  0.9047198589
]
 
var a = [1.00000000, -2.77555756e-16, 3.33333333e-01, -1.85037171e-17]
var b = [0.16666667,  0.5,            0.5,             0.16666667    ]
var f = TDF_II_filter(signal, a, b)
 
say "["
say f.map { "% 0.8f" % _ }.slices(5).map{.join(', ')}.join(",\n")
say "]"
```

#### Output:
```
[
-0.15297399, -0.43525783, -0.13604340,  0.69750333,  0.65644469,
-0.43548245, -1.08923946, -0.53767655,  0.51704999,  1.05224975,
 0.96185430,  0.69569009,  0.42435630,  0.19626223, -0.02783512,
-0.21172192, -0.17474556,  0.06925841,  0.38544587,  0.65177084
]
```