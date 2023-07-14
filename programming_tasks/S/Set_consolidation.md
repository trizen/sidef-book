[1]: https://rosettacode.org/wiki/Set_consolidation

# [Set consolidation][1]

```ruby
func consolidate() { [] }
func consolidate(this, *those) {
    gather {
        consolidate(those...).each { |that|
            if (this & that) { this |= that }
            else             { take that }
        }
        take this
    }
}
 
enum |A="A", B, C, D, _E, F, G, H, I, _J, K|
 
func format(ss) {
    ss.map{ '(' + .join(' ') + ')' }.join(' ')
}
 
[
    [[A,B], [C,D]],
    [[A,B], [B,D]],
    [[A,B], [C,D], [D,B]],
    [[H,I,K], [A,B], [C,D], [D,B], [F,G,H]]
].each { |ss|
    say (format(ss), "\n\t==> ", format(consolidate(ss...)))
}
```

#### Output:
```
(A B) (C D)
    ==> (C D) (A B)
(A B) (B D)
    ==> (A B D)
(A B) (C D) (D B)
    ==> (A B C D)
(H I K) (A B) (C D) (D B) (F G H)
    ==> (A B C D) (H I K F G)
```
