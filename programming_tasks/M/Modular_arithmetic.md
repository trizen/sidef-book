[1]: https://rosettacode.org/wiki/Modular_arithmetic

# [Modular arithmetic][1]

```ruby
class Modulo(n=0, m=13) {
 
  method init {
     (n, m) = (n % m, m)
  }
 
  method to_n { n }
 
  < + - * ** >.each { |meth|
      Modulo.def_method(meth, method(n2) { Modulo(n.(meth)(n2.to_n), m) })
  }
 
  method to_s { "#{n} 「mod #{m}」" }
}
 
func f(x) { x**100 + x + 1 }
say f(Modulo(10, 13))
```

#### Output:
```
1 「mod 13」
```