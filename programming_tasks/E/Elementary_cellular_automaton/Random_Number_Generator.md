[1]: http://rosettacode.org/wiki/Elementary_cellular_automaton/Random_Number_Generator

# [Elementary cellular automaton/Random Number Generator][1]

```ruby
var auto = Automaton(30, [1] + 100.of(0));
 
10.times {
    var sum = 0;
    8.times {
        sum = (2*sum + auto.cells[0]);
        auto.next;
    };
    say sum;
};
```

#### Output:
```
220
197
147
174
117
97
149
171
240
241
```