[1]: http://rosettacode.org/wiki/Josephus_problem

# [Josephus problem][1]

Iterative:

```ruby
func josephus(n, k) {
    var prisoners = @^n
    while (prisoners.len > 1) {
        prisoners.rotate!(k - 1).shift
    }
    return prisoners[0]
}
```


Recursive:

```ruby
func josephus(n, k) {
    n == 1 ? 0 : ((__FUNC__(n-1, k) + k) % n)
}
```


Calling the function:

```ruby
var survivor = josephus(41, 3)
say "Prisoner #{survivor} survived."
```

#### Output:
```
Prisoner 30 survived.
```
