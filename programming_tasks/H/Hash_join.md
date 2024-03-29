[1]: https://rosettacode.org/wiki/Hash_join

# [Hash join][1]

```ruby
func hashJoin(table1, index1, table2, index2) {
    var a = []
    var h = Hash()
 
    # hash phase
    table1.each { |s|
        h{s[index1]} := [] << s
    }
 
    # join phase
    table2.each { |r|
        a += h{r[index2]}.map{[_,r]}
    }
 
    return a
}
 
var t1  = [[27, "Jonah"],
           [18, "Alan"],
           [28, "Glory"],
           [18, "Popeye"],
           [28, "Alan"]]
 
var t2  = [["Jonah", "Whales"],
           ["Jonah", "Spiders"],
           ["Alan", "Ghosts"],
           ["Alan", "Zombies"],
           ["Glory", "Buffy"]]
 
hashJoin(t1, 1, t2, 0).each { .say }
```

#### Output:
```
[[27, 'Jonah'], ['Jonah', 'Whales']]
[[27, 'Jonah'], ['Jonah', 'Spiders']]
[[18, 'Alan'], ['Alan', 'Ghosts']]
[[28, 'Alan'], ['Alan', 'Ghosts']]
[[18, 'Alan'], ['Alan', 'Zombies']]
[[28, 'Alan'], ['Alan', 'Zombies']]
[[28, 'Glory'], ['Glory', 'Buffy']]
```
