[1]: https://rosettacode.org/wiki/Dice_game_probabilities

# [Dice game probabilities][1]

```ruby
func combos(sides, n) {
    n || return [1]
    var ret = ([0] * (n*sides.max + 1))
    combos(sides, n-1).each_kv { |i,v|
        v && for s in sides { ret[i + s] += v }
    }
    return ret
}
 
func winning(sides1, n1, sides2, n2) {
    var (p1, p2) = (combos(sides1, n1), combos(sides2, n2))
    var (win,loss,tie) = (0,0,0)
    p1.each_kv { |i, x|
        win  += x*p2.ft(0,i-1).sum
        tie  += x*p2.ft(i, i).sum
        loss += x*p2.ft(i+1).sum
    }
    [win, tie, loss] »/» p1.sum*p2.sum
}
 
func display_results(String title, Array res) {
    say "=> #{title}"
    for name, prob in (%w(p₁\ win tie p₂\ win) ~Z res) {
        say "P(#{'%6s' % name}) =~ #{prob.round(-11)} (#{prob.as_frac})"
    }
    print "\n"
}
 
display_results('9D4 vs 6D6',  winning(range(1, 4), 9, range(1,6), 6))
display_results('5D10 vs 6D7', winning(range(1,10), 5, range(1,7), 6))
```

#### Output:
```
=> 9D4 vs 6D6
P(p₁ win) =~ 0.57314407678 (48679795/84934656)
P(   tie) =~ 0.07076616984 (144252007/2038431744)
P(p₂ win) =~ 0.35608975338 (725864657/2038431744)

=> 5D10 vs 6D7
P(p₁ win) =~ 0.64278862872 (3781171969/5882450000)
P(   tie) =~ 0.04449603031 (523491347/11764900000)
P(p₂ win) =~ 0.31271534097 (735812943/2352980000)
```
