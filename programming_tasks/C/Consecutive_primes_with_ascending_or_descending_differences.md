[1]: https://rosettacode.org/wiki/Consecutive_primes_with_ascending_or_descending_differences

# [Consecutive primes with ascending or descending differences][1]

```ruby
func runs(f, arr) {
 
    var run = 0
    var diff = 0
    var diffs = []
 
    arr.each_cons(2, {|p1,p2|
        var curr_diff = (p2 - p1)
        f(curr_diff, diff) ? ++run : (run = 1)
        diff = curr_diff
        diffs << run
    })
 
    var max  = diffs.max
    var runs = []
 
    diffs.indices_by { _ == max }.each {|i|
        runs << arr.slice(i - max + 1, i + 1)
    }
 
    return runs
}
 
var limit = 1e6
var primes = limit.primes
 
say "Longest run(s) of ascending prime gaps up to #{limit.commify}:"
say runs({|a,b| a > b }, primes).join("\n")
 
say "\nLongest run(s) of descending prime gaps up to #{limit.commify}:"
say runs({|a,b| a < b }, primes).join("\n")
```

#### Output:
```
Longest run(s) of ascending prime gaps up to 1,000,000:
[128981, 128983, 128987, 128993, 129001, 129011, 129023, 129037]
[402581, 402583, 402587, 402593, 402601, 402613, 402631, 402691]
[665111, 665113, 665117, 665123, 665131, 665141, 665153, 665177]

Longest run(s) of descending prime gaps up to 1,000,000:
[322171, 322193, 322213, 322229, 322237, 322243, 322247, 322249]
[752207, 752251, 752263, 752273, 752281, 752287, 752291, 752293]
```
