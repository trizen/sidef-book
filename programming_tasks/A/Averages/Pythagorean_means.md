[1]: http://rosettacode.org/wiki/Averages/Pythagorean_means

# [Averages/Pythagorean means][1]

```ruby
func A(a) { a.sum / a.len }
func G(a) { a.prod.root(a.len) }
func H(a) { a.len / a.map{1/_}.sum }
```


The same thing, using hyper-operators:

```ruby
func A(a) { a«+» / a.len }
func G(a) { a«*» ** (1/a.len) }
func H(a) { a.len / (a«/«1 «+») }
```


Calling the functions:

```ruby
say("A(1,...,10) = ", A(1..10))
say("G(1,...,10) = ", G(1..10))
say("H(1,...,10) = ", H(1..10))
```

#### Output:
```
A(1,...,10) = 5.5
G(1,...,10) = 4.528728688116764762203309337195508793499
H(1,...,10) = 3.414171521474055006096734859775098225173
```
