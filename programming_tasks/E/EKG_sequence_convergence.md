[1]: https://rosettacode.org/wiki/EKG_sequence_convergence

# [EKG sequence convergence][1]

```ruby
class Seq(terms, callback) {
    method next {
        terms += callback(terms)
    }
 
    method nth(n) {
        while (terms.len < n) {
            self.next
        }
        terms[n-1]
    }
 
    method first(n) {
        while (terms.len < n) {
            self.next
        }
        terms.first(n)
    }
}
 
func next_EKG (s) {
    2..Inf -> first {|k|
        !(s.contains(k) || s[-1].is_coprime(k))
    }
}
 
func EKG (start) {
    Seq([1, start], next_EKG)
}
 
func converge_at(ints) {
    var ekgs = ints.map(EKG)
 
    2..Inf -> first {|k|
        (ekgs.map { .nth(k)        }.uniq.len == 1) &&
        (ekgs.map { .first(k).sort }.uniq.len == 1)
    }
}
 
for k in [2, 5, 7, 9, 10] {
    say "EKG(#{k}) = #{EKG(k).first(10)}"
}
 
for arr in [[5,7], [2, 5, 7, 9, 10]] {
    var c = converge_at(arr)
    say "EKGs of #{arr} converge at term #{c}"
}
```

#### Output:
```
EKG(2) = [1, 2, 4, 6, 3, 9, 12, 8, 10, 5]
EKG(5) = [1, 5, 10, 2, 4, 6, 3, 9, 12, 8]
EKG(7) = [1, 7, 14, 2, 4, 6, 3, 9, 12, 8]
EKG(9) = [1, 9, 3, 6, 2, 4, 8, 10, 5, 15]
EKG(10) = [1, 10, 2, 4, 6, 3, 9, 12, 8, 14]
EKGs of [5, 7] converge at term 21
EKGs of [2, 5, 7, 9, 10] converge at term 45
```