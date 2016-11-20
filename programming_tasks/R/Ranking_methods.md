[1]: http://rosettacode.org/wiki/Ranking_methods

# [Ranking methods][1]

```ruby
var scores = [
    Pair(Solomon => 44),
    Pair(Jason   => 42),
    Pair(Errol   => 42),
    Pair(Garry   => 41),
    Pair(Bernard => 41),
    Pair(Barry   => 41),
    Pair(Stephen => 39),
]
 
func tiers(s) {
    s.group_by { .value }.kv.sort.flip.map { .value.map{.key} }
}
 
func standard(s) {
    var rank = 1
    gather {
        for players in tiers(s) {
            take(Pair(rank, players))
            rank += players.len
        }
    }
}
 
func modified(s) {
    var rank = 0
    gather {
        for players in tiers(s) {
            rank += players.len
            take(Pair(rank, players))
        }
    }
}
 
func dense(s) {
    tiers(s).map_kv { |k,v| Pair(k+1, v) }
}
 
func ordinal(s) {
    s.map_kv { |k,v| Pair(k+1, v.key) }
}
 
func fractional(s) {
    var rank = 1
    gather {
        for players in tiers(s) {
            var beg = rank
            var end = (rank += players.len)
            take(Pair(sum(beg ..^ end) / players.len, players))
        }
    }
}
 
func display(r) {
    say r.map {|a| '%3s : %s' % a... }.join("\n")
}
 
say   "Standard:";   display(  standard(scores))
say "\nModified:";   display(  modified(scores))
say "\nDense:";      display(     dense(scores))
say "\nOrdinal:";    display(   ordinal(scores))
say "\nFractional:"; display(fractional(scores))
```

#### Output:
```
Standard:
  1 : ["Solomon"]
  2 : ["Jason", "Errol"]
  4 : ["Garry", "Bernard", "Barry"]
  7 : ["Stephen"]

Modified:
  1 : ["Solomon"]
  3 : ["Jason", "Errol"]
  6 : ["Garry", "Bernard", "Barry"]
  7 : ["Stephen"]

Dense:
  1 : ["Solomon"]
  2 : ["Jason", "Errol"]
  3 : ["Garry", "Bernard", "Barry"]
  4 : ["Stephen"]

Ordinal:
  1 : Solomon
  2 : Jason
  3 : Errol
  4 : Garry
  5 : Bernard
  6 : Barry
  7 : Stephen

Fractional:
  1 : ["Solomon"]
2.5 : ["Jason", "Errol"]
  5 : ["Garry", "Bernard", "Barry"]
  7 : ["Stephen"]
```