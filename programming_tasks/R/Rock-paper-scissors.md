[1]: http://rosettacode.org/wiki/Rock-paper-scissors

# [Rock-paper-scissors][1]

```ruby
const rps = %w(r p s)

const msg = [
    "Rock breaks scissors",
    "Paper covers rock",
    "Scissors cut paper",
]

say <<"EOT"
\n>> Rock Paper Scissors <<\n
** Enter 'r', 'p', or 's' as your play.
** Enter 'q' to exit the game.
** Running score shown as <your wins>:<my wins>
EOT

var plays   = 0
var aScore  = 0
var pScore  = 0
var pcf     = [0,0,0]      # pcf = player choice frequency
var aChoice = pick(0..2)   # ai choice for first play is completely random

loop {
    var pi = Sys.scanln("Play: ")
    pi == 'q' && break

    var pChoice = rps.index(pi)

    if (pChoice == -1) {
        STDERR.print("Invalid input!\n")
        next
    }

    ++pcf[pChoice]
    ++plays

    # show result of play
    ">> My play: %-8s".printf(rps[aChoice])

    given ((aChoice - pChoice + 3) % 3) {
        when (0) { say "Tie." }
        when (1) { "%-*s %s".printlnf(30, msg[aChoice], 'My point');   aScore++ }
        when (2) { "%-*s %s".printlnf(30, msg[pChoice], 'Your point'); pScore++ }
    }

    # show score
    "%-6s".printf("%d:%d" % (pScore, aScore))

    # compute ai choice for next play
    given (plays.rand.int) { |rn|
        case (rn < pcf[0])        { aChoice = 1 }
        case (pcf[0]+pcf[1] > rn) { aChoice = 2 }
        default                   { aChoice = 0 }
    }
}
```


*Sample run:*


#### Output:
```
>> Rock Paper Scissors <<

** Enter 'r', 'p', or 's' as your play.
** Enter 'q' to exit the game.
** Running score shown as <your wins>:<my wins>

Play: r
>> My play: s       Rock breaks scissors           Your point
1:0   Play: p
>> My play: p       Tie.
1:0   Play: r
>> My play: s       Rock breaks scissors           Your point
2:0   Play: s
>> My play: p       Scissors cut paper             Your point
3:0   Play: r
>> My play: p       Paper covers rock              My point
3:1   Play: p
>> My play: r       Paper covers rock              Your point
4:1   Play: q
```
