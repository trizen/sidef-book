[1]: https://rosettacode.org/wiki/Standard_deviation

# [Standard deviation][1]

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
adding 4: stddev of 3 samples is 0.9428090415820633658677924828064653857143
adding 4: stddev of 4 samples is 0.8660254037844386467637231707529361834714
adding 5: stddev of 5 samples is 0.9797958971132712392789136298823565567864
adding 5: stddev of 6 samples is 1
adding 7: stddev of 7 samples is 1.399708424447530341827019471260509366836
adding 9: stddev of 8 samples is 2
```


Using _static_ variables:

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
0.9428090415820633658677924828064653857143
0.8660254037844386467637231707529361834714
0.9797958971132712392789136298823565567864
1
1.399708424447530341827019471260509366836
2
```
