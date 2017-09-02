[1]: https://rosettacode.org/wiki/Conjugate_transpose

# [Conjugate transpose][1]

```ruby
func is_Hermitian (Array m, Array t) -> Bool { m == t }
 
func mat_mult (Array a, Array b, Number ε = -3) {
    var p = []
    for r, c in (^a ~X ^b[0]) {
        for k in (^b) {
            p[r][c] := 0 += (a[r][k] * b[k][c]) -> round!(ε)
        }
    }
    return p
}
 
func mat_trans (Array m) {
    var r = []
    for i,j in (^m ~X ^m[0]) {
        r[j][i] = m[i][j]
    }
    return r
}
 
func mat_ident (Number n) {
    ^n -> map {|i|
        [i.of(0)..., 1, (n - i - 1).of(0)...]
    }
}
 
func is_Normal (Array m, Array t) -> Bool {
    mat_mult(m, t) == mat_mult(t, m)
}
 
func is_Unitary (Array m, Array t) -> Bool {
    mat_mult(m, t) == mat_ident(m.len)
}
 
func say_it (Array a) {
    a.each {|b|
        b.map { "%9s" % _ }.join(' ').say
    }
}
 
[
    [
       [   1, 1+1i, 2i],
       [1-1i,    5, -3],
       [0-2i,   -3,  0]
    ],
    [
       [1, 1, 0],
       [0, 1, 1],
       [1, 0, 1]
    ],
    [
       [0.707 ,   0.707,  0],
       [0.707i, -0.707i,  0],
       [0     ,       0,  1i]
    ]
].each { |m|
    say "\nMatrix:"
    say_it(m)
    var t = mat_trans(m.map{.map{.conj}})
    say "\nTranspose:"
    say_it(t)
    say "Is Hermitian?\t#{is_Hermitian(m, t)}"
    say "Is Normal?\t#{is_Normal(m, t)}"
    say "Is Unitary?\t#{is_Unitary(m, t)}"
}
```

#### Output:
```
Matrix:
        1       1+i        2i
      1-i         5        -3
      -2i        -3         0

Transpose:
        1       1+i        2i
      1-i         5        -3
      -2i        -3         0
Is Hermitian?   true
Is Normal?      true
Is Unitary?     false

Matrix:
        1         1         0
        0         1         1
        1         0         1

Transpose:
        1         0         1
        1         1         0
        0         1         1
Is Hermitian?   false
Is Normal?      true
Is Unitary?     false

Matrix:
    0.707     0.707         0
   0.707i   -0.707i         0
        0         0         i

Transpose:
    0.707   -0.707i         0
    0.707    0.707i         0
        0         0        -i
Is Hermitian?   false
Is Normal?      true
Is Unitary?     true
```