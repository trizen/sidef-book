[1]: https://rosettacode.org/wiki/Diversity_prediction_theorem

# [Diversity prediction theorem][1]

```ruby
func avg_error(m, v) {
    v.map { (_ - m)**2 }.sum / v.len
}
 
func diversity_calc(truth, pred) {
    var ae = avg_error(truth, pred)
    var cp = pred.sum/pred.len
    var ce = (cp - truth)**2
    var pd = avg_error(cp, pred)
    return [ae, ce, pd]
}
 
func diversity_format(stats) {
    gather {
        for t,v in (%w(average-error crowd-error diversity) ~Z stats) {
            take(("%13s" % t) + ':' + ('%7.3f' % v))
        }
    }
}
 
diversity_format(diversity_calc(49, [48, 47, 51])).each{.say}
diversity_format(diversity_calc(49, [48, 47, 51, 42])).each{.say}
```

#### Output:
```
average-error:  3.000
  crowd-error:  0.111
    diversity:  2.889
average-error: 14.500
  crowd-error:  4.000
    diversity: 10.500
```