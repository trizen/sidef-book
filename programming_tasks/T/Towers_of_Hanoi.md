[1]: https://rosettacode.org/wiki/Towers_of_Hanoi

# [Towers of Hanoi][1]

```ruby
func hanoi(n, from=1, to=2, via=3) {
    if (n == 1) {
        say "Move disk from pole #{from} to pole #{to}."
    } else {
        hanoi(n-1, from, via,   to)
        hanoi(  1, from,  to,  via)
        hanoi(n-1,  via,  to, from)
    }
}
 
hanoi(4)
```
