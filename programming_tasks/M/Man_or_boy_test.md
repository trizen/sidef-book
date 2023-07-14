[1]: https://rosettacode.org/wiki/Man_or_boy_test

# [Man or boy test][1]

```ruby
func a(k, x1, x2, x3, x4, x5) {
    func b { a(--k, b, x1, x2, x3, x4) }
    k <= 0 ? (x4() + x5()) : b()
}
say a(10, ->{1}, ->{-1}, ->{-1}, ->{1}, ->{0})      #=> -67
```


This solution avoids creating the closure b if k &lt;= 0 (that is, nearly every time).

```ruby
func a(k, x1, x2, x3, x4, x5) {
    k <= 0 ? (x4() + x5())
           : func b { a(--k, b, x1, x2, x3, x4) }()
}
say a(10, ->{1}, ->{-1}, ->{-1}, ->{1}, ->{0})      #=> -67
```


Alternatively, we can implement it as a method too:

```ruby
class MOB {
    method a(k, x1, x2, x3, x4, x5) {
        func b { self.a(--k, b, x1, x2, x3, x4) }
        k <= 0 ? (x4() + x5()) : b()
    }
}
 
var obj = MOB()
say obj.a(10, ->{1}, ->{-1}, ->{-1}, ->{1}, ->{0})
```
