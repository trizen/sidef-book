[1]: https://rosettacode.org/wiki/Best_shuffle

# [Best shuffle][1]

```ruby
func best_shuffle(String orig) -> (String, Number) {

    var s = orig.chars
    var t = s.shuffle

    for i (^s) {
        for j (^s) {
            if (i!=j && t[i]!=s[j] && t[j]!=s[i]) {
                t[i, j] = t[j, i]
                break
            }
        }
    }

    (t.join, s ~Z== t -> count(true))
}

for word (<abracadabra seesaw elk grrrrrr up a>) {
    var (sword, score) = best_shuffle(word)
    "%-12s %12s: %d\n".printf(word, sword, score)
}
```

#### Output:
```
abracadabra   daabacarrab: 0
seesaw             esaews: 0
elk                   lke: 0
grrrrrr           rgrrrrr: 5
up                     pu: 0
a                       a: 1
```
