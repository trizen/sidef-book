[1]: https://rosettacode.org/wiki/Smarandache-Wellin_primes

# [Smarandache-Wellin primes][1]

```ruby
say "Smarandache-Wellen primes:"

for (var (p=2, i=1, n='', nth=1); nth <= 8; (p.next_prime!, ++i)) {
    n += Str(p)
    if (Num(n).is_prime){
        var t = n
        if (t.len > 50) {
            t = (t.first(20) + ' ... ' + t.last(20) + " (#{t.len} digits)")
        }
        printf("%s: Index:%5d  Last prime:%6d  S-W: %s\n", nth, i, p, t)
        ++nth
    }
}

say "\nSmarandache-Wellen derived primes:"

func derived(String n) -> String {
    var freq = n.chars.freq
    0..9 -> map { freq{_} \\ 0 }.join
}

for (var (p=2, i=1, nth=1, n=''); nth <= 20; (p.next_prime!, ++i)) {
    n += Str(p)
    var t = derived(n)
    if (Num(t).is_prime){
        if (t.len > 50) {
            t = (t.first(20) + ' ... ' + t.last(20) + " (#{t.len} digits)")
        }
        printf("%2s: Index:%5d  %s\n", nth, i, t)
        ++nth
    }
}
```

#### Output:
```
Smarandache-Wellen primes:
1: Index:    1  Last prime:     2  S-W: 2
2: Index:    2  Last prime:     3  S-W: 23
3: Index:    4  Last prime:     7  S-W: 2357
4: Index:  128  Last prime:   719  S-W: 23571113171923293137 ... 73677683691701709719 (355 digits)
5: Index:  174  Last prime:  1033  S-W: 23571113171923293137 ... 10131019102110311033 (499 digits)
6: Index:  342  Last prime:  2297  S-W: 23571113171923293137 ... 22732281228722932297 (1171 digits)
7: Index:  435  Last prime:  3037  S-W: 23571113171923293137 ... 30013011301930233037 (1543 digits)
8: Index: 1429  Last prime: 11927  S-W: 23571113171923293137 ... 11903119091192311927 (5719 digits)

Smarandache-Wellen derived primes:
 1: Index:   32  4194123321127
 2: Index:   72  547233879626521
 3: Index:   73  547233979727521
 4: Index:  134  13672766322929571043
 5: Index:  225  3916856106393739943689
 6: Index:  303  462696313560586013558131
 7: Index:  309  532727113760586013758133
 8: Index:  363  6430314317473636515467149
 9: Index:  462  8734722823685889120488197
10: Index:  490  9035923128899919621189209
11: Index:  495  9036023329699969621389211
12: Index:  522  9337023533410210710923191219
13: Index:  538  94374237357103109113243102223
14: Index:  624  117416265406198131121272110263
15: Index:  721  141459282456260193137317129313
16: Index:  738  144466284461264224139325131317
17: Index:  790  156483290479273277162351153339
18: Index:  852  164518312512286294233375158359
19: Index: 1087  208614364610327343341589284471
20: Index: 1188  229667386663354357356628334581
```
