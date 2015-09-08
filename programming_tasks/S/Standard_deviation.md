[1]: http://rosettacode.org/wiki/Standard_deviation

# [Standard deviation][1]

```ruby
func stddev(x) {
    static(num, sum, sum2) = 3.of(0)...;
    num++;
    sqrt(
        (sum2 += x**2) / num -
        (((sum += x) / num)**2)
    );
}
 
%n(2 4 4 4 5 5 7 9).each { say stddev(_) };
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