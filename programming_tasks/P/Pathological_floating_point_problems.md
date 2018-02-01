[1]: https://rosettacode.org/wiki/Pathological_floating_point_problems

# [Pathological floating point problems][1]

**Muller's sequence**

```ruby
func series (n) {
    var (u, v) = (2, -4)
    (n-2).times { (u, v) = (v, 111 - 1130/v + 3000/(v * u)) }
    return v
}
 
[(3..8)..., 20, 30, 50, 100].each {|n|
    printf("n = %3d -> %s\n", n, series(n))
}
```

#### Output:
```
n =   3 -> 18.5
n =   4 -> 9.3783783783783783783783783783783783783783783783784
n =   5 -> 7.801152737752161383285302593659942363112391930836
n =   6 -> 7.154414480975249353527890653860362024381233838197
n =   7 -> 6.806784736923632983941756596272009087623276707802
n =   8 -> 6.592632768704438392742002776365994826552982317735
n =  20 -> 6.043552110189268867777477364097540133187715000006
n =  30 -> 6.006786093031205758530554047953239705833072314438
n =  50 -> 6.000175846627187188945614020747195469523735177099
n = 100 -> 6.000000019319477929104086803403585715024350675437
```


**The Chaotic Bank Society**

```ruby
var years = 25
var balance = (1 .. years+15 -> sum_by {|n| 1 / n! })
say "Starting balance, $(e-1): $#{balance}"
for i in (1..years) { balance = (i*balance - 1) }
printf("After year %d, you will have $%1.16g in your account.\n", years, balance)
```

#### Output:
```
Starting balance, $(e-1): $1.7182818284590452353602874713526624977572470937
After year 25, you will have $0.03993872967323021 in your account.
```


**Siegfried Rump's example**

```ruby
func f (a, b) {
    (333.75 * b**6) + (a**2 * ((11 * a**2 * b**2) -
      b**6 - (121 * b**4) - 2)) + (5.5 * b**8) + a/(2*b)
}
 
say f(77617.0, 33096.0)
```

#### Output:
```
-0.8273960599468213681411650954798162919990331157844
```