[1]: http://rosettacode.org/wiki/Pig_the_dice_game/Player

# [Pig the dice game/Player][1]

```ruby
var (games=100) = @ARGV.map{.to_i};
 
define DIE = 1..6;
define GOAL = 100;
 
class Player(score=0, ante, rolls, strategy={false}) {
    method turn {
        rolls = 0;
        ante  = 0;
        loop {
            rolls++;
            given (var roll = DIE.rand) {
                when (1) {
                    ante = 0;
                    break;
                }
                when (roll > 1) {
                    ante += roll;
                }
            }
            ((score + ante >= GOAL) || strategy) && break;
        }
        score += ante;
    }
}
 
var players = [];
 
# default, go-for-broke, always roll again
players[0] = Player.new;
 
# try to roll 5 times but no more per turn
players[1] = Player.new( strategy: { players[1].rolls >= 5 } );
 
# try to accumulate at least 20 points per turn
players[2] = Player.new( strategy: { players[2].ante > 20 } );
 
# random but 90% chance of rolling again
players[3] = Player.new( strategy: { 1.rand < 0.1 } );
 
# random but more conservative as approaches goal
players[4] = Player.new( strategy: { 1.rand < ((GOAL - players[4].score) * 0.6 / GOAL) } );
 
var wins = [0]*players.len;
 
games.times {
    var player = -1;
    loop {
        player++;
        var p = players[player % players.len];
        p.turn;
        p.score >= GOAL && break;
    }
    wins[player % players.len]++;
    players.map{.score}.join("\t").say;
    players.each { |p| p.score = 0 };
}
 
"\nSCORES: for #{games} games".say;
wins.join("\t").say;
```

#### Output:
```
0       0       67      101     19
0       88      100     9       14
0       81      66      100     24
0       56      103     8       27
0       102     70      17      27
0       79      101     29      36
0       100     71      56      31
0       62      104     28      34
103     19      24      6       5
0       49      101     24      19
0       60      22      101     0
0       20      101     30      34
...
...
...
0       101     69      26      91
0       87      101     30      54
0       84      100     17      64
0       52      24      102     17

SCORES: for 100 games
6       28      40      22      4
```