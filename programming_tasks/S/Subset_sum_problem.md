[1]: https://rosettacode.org/wiki/Subset_sum_problem

# [Subset sum problem][1]

```ruby
var pairs = Hash(
    alliance    => -624, archbishop => -915,
    brute       =>  870, centipede  => -658,
    departure   =>  952, deploy     =>   44,
    elysee      => -326, eradicate  =>  376,
    fiat        =>  170, filmy      => -874,
    infra       => -847, isis       => -982,
    mincemeat   => -880, moresby    =>  756,
    smokescreen =>  423, speakeasy  => -745,
    balm        =>  397, bonnet     =>  452,
    cobol       =>  362, covariate  =>  590,
    diophantine =>  645, efferent   =>   54,
    escritoire  =>  856, exorcism   => -983,
    flatworm    =>  503, gestapo    =>  915,
    lindholm    =>  999, markham    =>  475,
    mycenae     =>  183, plugging   => -266,
    vein        =>  813,
)

var weights = pairs.keys.sort.map{|k| pairs{k} }
var inverse = pairs.flip

for n in (1 .. weights.end) {
    var found = false
    weights.combinations(n, {|*comb|
        if (comb.sum == 0) {
            say "Length #{n}: "+" ".join(inverse{comb...})
            found = true
            break
        }
    })
    found || say "Length #{n}: (none)"
}
```

#### Output:
```
Length 1: (none)
Length 2: archbishop gestapo
Length 3: centipede markham mycenae
Length 4: alliance balm deploy mycenae
Length 5: alliance brute covariate deploy mincemeat
Length 6: alliance archbishop balm deploy gestapo mycenae
Length 7: alliance archbishop bonnet cobol departure exorcism moresby
Length 8: alliance archbishop balm bonnet fiat flatworm isis lindholm
...
```
