[1]: https://rosettacode.org/wiki/Evolutionary_algorithm

# [Evolutionary algorithm][1]

```ruby
define target = "METHINKS IT IS LIKE A WEASEL"
define mutate_chance = 0.08
define alphabet = [@|('A'..'Z'), ' ']
define C = 100

func fitness(str) { str.chars ~Z== target.chars -> count(true) }
func mutate(str)  { str.gsub(/(.)/, {|s1| 1.rand < mutate_chance ? alphabet.pick : s1 }) }

for (
    var (i, parent) = (0, alphabet.rand(target.len).join);
    parent != target;
    parent = C.of{ mutate(parent) }.max_by(fitness)
) { printf("%6d: '%s'\n", i++, parent) }
```
