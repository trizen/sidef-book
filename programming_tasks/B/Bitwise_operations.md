[1]: http://rosettacode.org/wiki/Bitwise_operations

# [Bitwise operations][1]

```ruby
func bitwise(a, b) {
   say ('a and b : ',  a & b)
   say ('a or b  : ',  a | b)
   say ('a xor b : ',  a ^ b)
   say ('not a   : ',     ~a)
   say ('a << b  : ', a << b)  # left shift
   say ('a >> b  : ', a >> b)  # arithmetic right shift
}
 
bitwise(14,3)
```

#### Output:
```
a and b : 2
a or b  : 15
a xor b : 13
not a   : -15
a << b  : 112
a >> b  : 1
```
