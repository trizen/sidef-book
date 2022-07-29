[1]: https://rosettacode.org/wiki/Anadromes

# [Anadromes][1]

```ruby
var S = Hash()
 
File('words.txt').open_r.each {|word|
    word.len > 6 || next
    if (S.has(word.flip)) {
        say "#{word.flip} <=> #{word}"
    }
    else {
        S{word} = true
    }
}
```

#### Output:
```
amaroid <=> diorama
gateman <=> nametag
deifier <=> reified
leveler <=> relevel
deviler <=> relived
degener <=> reneged
relever <=> reveler
deliver <=> reviled
reliver <=> reviler
redrawer <=> rewarder
dioramas <=> samaroid
revotes <=> setover
sallets <=> stellas
reknits <=> stinker
desserts <=> stressed
pat-pat <=> tap-tap
dessert <=> tressed
```
