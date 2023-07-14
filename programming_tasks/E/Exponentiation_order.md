[1]: https://rosettacode.org/wiki/Exponentiation_order

# [Exponentiation order][1]

In Sidef, the whitespace between the operands and the operator controls the precedence of the operation.

```ruby
var a = [
    '5**3**2',
    '(5**3)**2',
    '5**(3**2)',
    '5 ** 3 ** 2',
    '5 ** 3**2',
    '5**3 ** 2',
    '[5,3,2]«**»',
]
 
a.each {|e|
    "%-12s == %s\n".printf(e, eval(e))
}
```

#### Output:
```
5**3**2      == 1953125
(5**3)**2    == 15625
5**(3**2)    == 1953125
5 ** 3 ** 2  == 15625
5 ** 3**2    == 1953125
5**3 ** 2    == 15625
[5,3,2]«**»  == 15625
```