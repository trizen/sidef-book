[1]: https://rosettacode.org/wiki/Even_numbers_which_cannot_be_expressed_as_the_sum_of_two_twin_primes

# [Even numbers which cannot be expressed as the sum of two twin primes][1]

```ruby
var limit = 1e4

func display(msg, sums) {
    say msg
    2..limit -> by(2).grep{ !sums.has(_) }.each_slice(10, {|*s|
        say s.map{ '%4s' % _ }.join(' ')
    })
}

var sums = Set()
var twins = primes(3, limit).cons(2).grep{ .diffs[0] == 2 }.flat.uniq

[twins, twins].cartesian{|a,b| sums << a+b }
display("Non twin prime sums:", sums)

sums << (2, twins.map{.inc}...)
display("\nNon twin prime sums (including 1):", sums)
```

#### Output:
```
Non twin prime sums:
   2    4   94   96   98  400  402  404  514  516
 518  784  786  788  904  906  908 1114 1116 1118
1144 1146 1148 1264 1266 1268 1354 1356 1358 3244
3246 3248 4204 4206 4208

Non twin prime sums (including 1):
  94   96   98  400  402  404  514  516  518  784
 786  788  904  906  908 1114 1116 1118 1144 1146
1148 1264 1266 1268 1354 1356 1358 3244 3246 3248
4204 4206 4208
```
