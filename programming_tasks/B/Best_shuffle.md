[1]: http://rosettacode.org/wiki/Best_shuffle

# [Best shuffle][1]

```ruby
func best_shuffle(String orig) -> (String, Number) {

    var s = orig.chars
    var t = s.shuffle

    s.range.each { |i|
        s.range.each { |j|
            if (i!=j && t[i]!=s[j] && t[j]!=s[i]) {
                t[i, j] = t[j, i];
                break;
            }
        }
    }

    var word = t.join;
    (word, orig ^ word -> count("\0"));
}

<abracadabra seesaw elk grrrrrr up a>.each { |word|
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
