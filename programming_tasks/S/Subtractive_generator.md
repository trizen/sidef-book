[1]: https://rosettacode.org/wiki/Subtractive_generator

# [Subtractive generator][1]

```ruby
class SubRandom(seed, state=[]) {
 
    const mod = 1_000_000_000
 
    method init {
        var s = [seed % mod, 1]
        53.times {
            s.append((s[-2] - s[-1]) % mod)
        }
        state = s.range.map {|i| s[(34 + 34*i) % 55] }
        165.times { self.subrand }
    }
 
    method subrand {
        var x = ((state.shift - state[-24]) % mod)
        state.append(x)
        return x
    }
}
 
var r = SubRandom(292929)
10.times { say r.subrand }
```

#### Output:
```
467478574
512932792
539453717
20349702
615542081
378707948
933204586
824858649
506003769
380969305
```
