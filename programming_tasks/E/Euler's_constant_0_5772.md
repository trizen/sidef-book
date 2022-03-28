[1]: https://rosettacode.org/wiki/Euler%27s_constant_0.5772...

# [Euler's constant 0.5772...][1]

Built-in:

```ruby
# 100 decimals of precision
local Num!PREC = 4*100
say Num.EulerGamma
```

#### Output:
```
0.5772156649015328606065120900824024310421593359399235988057672348848677267776646709369470632917467495
```


Several formulas:

```ruby
const n = (ARGV ? Num(ARGV[0]) : 50)       # number of iterations
 
define ℯ = Num.e
define π = Num.pi
define γ = Num.EulerGamma
 
func display(r, t) {
    say "#{r}\terror: #{ '%.0g' % abs(r - t) }"
}
 
# Original definition of the Euler-Mascheroni constant, due to Euler (1731)
display(sum(1..n, {|n| 1/n }) - log(n), γ)
 
# Formula due to Euler (best convergence)
display(harmfrac(n) - log(n) - 1/(2*n) - sum(1..n, {|k|
    -bernoulli(2*k) / (2*k) / n**(2*k)
}), γ)
 
# Formula derived from the above formula of Euler,
# using approximations of Bernoulli numbers.
display(harmfrac(n) - log(n) - 1/(2*n) - sum(1..n, {|k|
    (-1)**k * 4 * sqrt(π*k) * (π * ℯ)**(-2*k) * k**(2*k) / (2*k) / n**(2*k)
}), γ)
 
# Euler-Mascheroni constant, involving zeta(n)
display(1 - sum(2..(n+1), {|n|
    (zeta(n) - 1) / n
}), γ)
 
# Limit_{n->Infinity} zeta((n+1)/n) - n} = gamma
display(zeta((n+1)/n) - n, γ)
 
# Series due to Euler (1731).
display(sum(2..(n+1), {|n|
    (-1)**n * zeta(n) / n
}),  γ)
 
# Formula due to Euler in terms of log(2) and the odd zeta values
display(3/4 - log(2)/2 + sum(1..n, {|n|
    (1 - 1/(2*n + 1)) * (zeta(2*n + 1) - 1)
}), γ)
 
# Formula due to Euler in terms of log(2) and the odd zeta values (VII)
display(log(2) - sum(1..n, {|n|
    zeta(2*n + 1) / (2*n + 1) / 2**(2*n)
}), γ)
 
# Formula due to Vacca (1910)
display(sum(1..n, {|n|
    (-1)**n * floor(log2(n)) / n
}), γ)
```

#### Output:
```
0.58718233290127899894172100505421724484389898107       error: 0.01
0.57721566490153286060651209008240243104215933594       error: 2e-58
0.577201775274185974649592917416402750312879661543      error: 1e-05
0.577215664901532868991217643213156967011395887777      error: 8e-18
0.57867004101560321761330253540741574969540128177       error: 0.001
0.567507841748305076772446986005418728718501189232      error: 0.01
0.577215664901532860606512090082272222693164663104      error: 1e-31
0.57721566490153286060651209008240496797924366087       error: 3e-33
0.611009392556929160631547597803236563977259982583      error: 0.03
```
