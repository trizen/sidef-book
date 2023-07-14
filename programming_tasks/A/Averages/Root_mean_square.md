[1]: https://rosettacode.org/wiki/Averages/Root_mean_square

# [Averages/Root mean square][1]

```ruby
func rms(a) {
    sqrt(a.map{.**2}.sum / a.len)
}
 
say rms(1..10)
```

#### Output:
```
6.20483682299542829806662097772473784992796529536
```
