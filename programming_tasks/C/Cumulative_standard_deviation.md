[1]: http://rosettacode.org/wiki/Cumulative_standard_deviation

# [Cumulative standard deviation][1]

Using an object to keep state:

```ruby
class StdDevAccumulator(n=0, sum=0, sumofsquares=0) {
  method <<(num) {
    n += 1
    sum += num
    sumofsquares += num**2
    self
  }
 
  method stddev {
    sqrt(sumofsquares/n - pow(sum/n, 2))
  }
 
  method to_s {
    self.stddev.to_s
  }
}
 
var i = 0
var sd = StdDevAccumulator()
[2,4,4,4,5,5,7,9].each {|n|
    say "adding #{n}: stddev of #{i+=1} samples is #{sd << n}"
}
```

#### Output:
```
adding 2: stddev of 1 samples is 0
adding 4: stddev of 2 samples is 1
adding 4: stddev of 3 samples is 0.942809041582063365867792482806465385713114583585
adding 4: stddev of 4 samples is 0.866025403784438646763723170752936183471402626905
adding 5: stddev of 5 samples is 0.979795897113271239278913629882356556786378992263
adding 5: stddev of 6 samples is 1
adding 7: stddev of 7 samples is 1.39970842444753034182701947126050936683768427466
adding 9: stddev of 8 samples is 2
```


Using *static* variables:

```ruby
func stddev(x) {
    static(num=0, sum=0, sum2=0)
    num++
    sqrt(
        (sum2 += x**2) / num -
        (((sum += x) / num)**2)
    )
}
 
%n(2 4 4 4 5 5 7 9).each { say stddev(_) }
```

#### Output:
```
0
1
0.942809041582063365867792482806465385713114583585
0.866025403784438646763723170752936183471402626905
0.979795897113271239278913629882356556786378992263
1
1.39970842444753034182701947126050936683768427466
2
```
