[1]: https://rosettacode.org/wiki/Least_m_such_that_n!_%2B_m_is_prime

# [Least m such that n! + m is prime][1]

```ruby
with (50) {|N|
    say "Least positive m such that n! + m is prime (first #{N}):"
    ^N -> map {|n|
        var f = n!; 1..Inf -> first {|k| f+k -> is_prime }
    }.each_slice(10, {|*s|
        say s.map{ '%3s' % _ }.join(' ')
    })
}

say ''; var prev = 0
for n in (1..5 -> map { 1e3*_ }) {
    var m = (prev..Inf -> lazy.map{|k|
        var f = k!; [k, f.next_prime - f]
    }.first {|k|
        k.tail >= n
    })
    say "First m > #{n} is #{m.tail} at position #{m.head}"
    prev = m.head
}
```

#### Output:
```
Least positive m such that n! + m is prime (first 50):
  1   1   1   1   5   7   7  11  23  17
 11   1  29  67  19  43  23  31  37  89
 29  31  31  97 131  41  59   1  67 223
107 127  79  37  97  61 131   1  43  97
 53   1  97  71  47 239 101 233  53  83

First m > 1000 is 1069 at position 107
First m > 2000 is 3391 at position 192
First m > 3000 is 3391 at position 192
First m > 4000 is 4943 at position 284
First m > 5000 is 5233 at position 384
```
