[1]: http://rosettacode.org/wiki/Averages/Root_mean_square

# [Averages/Root mean square][1]

```ruby
func rms(a) {
    Math.sqrt(a.map{.**2}.sum / a.len);
}
 
say rms(1..10);
```

#### Output:
```
6.204836822995428298066620977724737849928
```