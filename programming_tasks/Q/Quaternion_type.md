[1]: https://rosettacode.org/wiki/Quaternion_type

# [Quaternion type][1]

```ruby
class Quaternion(r, i, j, k) {
 
    func qu(*r) { Quaternion(r...) }
 
    method to_s  { "#{r} + #{i}i + #{j}j + #{k}k" }
    method reals { [r, i, j, k] }
    method conj  { qu(r, -i, -j, -k) }
    method norm  { self.reals.map { _*_ }.sum.sqrt }
 
    method ==(Quaternion b) { self.reals == b.reals }
 
    method +(Number     b) { qu(b+r, i, j, k) }
    method +(Quaternion b) { qu((self.reals ~Z+ b.reals)...) }
 
    method neg { qu(self.reals.map{ .neg }...) }
 
    method *(Number     b) { qu((self.reals»*»b)...) }
    method *(Quaternion b) {
        var (r,i,j,k) = b.reals...
        qu(sum(self.reals ~Z* [r, -i, -j, -k]),
           sum(self.reals ~Z* [i,  r,  k, -j]),
           sum(self.reals ~Z* [j, -k,  r,  i]),
           sum(self.reals ~Z* [k,  j, -i,  r]))
    }
}
 
var q  = Quaternion(1, 2, 3, 4)
var q1 = Quaternion(2, 3, 4, 5)
var q2 = Quaternion(3, 4, 5, 6)
var r  = 7
 
say "1) q norm  = #{q.norm}"
say "2) -q      = #{-q}"
say "3) q conj  = #{q.conj}"
say "4) q  + r  = #{q + r}"
say "5) q1 + q2 = #{q1 + q2}"
say "6) q  * r  = #{q  * r}"
say "7) q1 * q2 = #{q1 * q2}"
say "8) q1q2 #{ q1*q2 == q2*q1 ? '==' : '!=' } q2q1"
```

#### Output:
```
1) q norm  = 5.47722557505166113456969782800802133952744694998
2) -q      = -1 + -2i + -3j + -4k
3) q conj  = 1 + -2i + -3j + -4k
4) q  + r  = 8 + 2i + 3j + 4k
5) q1 + q2 = 5 + 7i + 9j + 11k
6) q  * r  = 7 + 14i + 21j + 28k
7) q1 * q2 = -56 + 16i + 24j + 26k
8) q1q2 != q2q1
```
