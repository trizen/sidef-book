[1]: https://rosettacode.org/wiki/Monty_Hall_problem

# [Monty Hall problem][1]

```ruby
var n = 1000                                  # number of times to play
var switchWins = (var stayWins = 0)           # sum of each strategy's wins
 
n.times {                                     # play the game n times
   var prize = pick(^3)
   var chosen = pick(^3)
 
   var show;
   do {
        show = pick(^3)
   } while (show ~~ [chosen, prize])
 
   given(chosen) {
     when (prize)                 { stayWins   += 1 }
     when ([3 - show - prize])    { switchWins += 1 }
     default                      { die "~ error ~" }
   }
}
 
say ("Staying wins %.2f%% of the time."   % (100.0 * stayWins   / n))
say ("Switching wins %.2f%% of the time." % (100.0 * switchWins / n))
```

#### Output:
```
Staying wins 30.10% of the time.
Switching wins 69.90% of the time.
```
