[1]: http://rosettacode.org/wiki/Sailors,_coconuts_and_a_monkey_problem

# [Sailors, coconuts and a monkey problem][1]

```ruby
func coconuts(sailors, monkeys=1) {
    if ((sailors < 2) || (monkeys < 1) || (sailors <= monkeys)) {
        return 0
    }
    var blue_cocos = sailors-1
    var pow_bc = blue_cocos**sailors
    var x_cocos = pow_bc
    while ((x_cocos-blue_cocos)%sailors || ((x_cocos-blue_cocos)/sailors < 1)) {
        x_cocos += pow_bc
    }
    return monkeys*(x_cocos / pow_bc * sailors**sailors - blue_cocos)
}

for sailor in (2..9) {
    say "#{sailor}: #{coconuts(sailor)}";
}
```

#### Output:
```
2: 11
3: 25
4: 765
5: 3121
6: 233275
7: 823537
8: 117440505
9: 387420481
```
