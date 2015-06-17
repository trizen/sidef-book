[1]: http://rosettacode.org/wiki/Van_der_Corput_sequence

# [Van der Corput sequence][1]

```ruby
func vdc(value, base=2) {
    while (value[-1] > 0) {
        value.append(value[-1] / base int);
    };
    var (x, sum) = (1, 0);
    value.each { |i|
        sum += ((i % base) / (x *= base));
    };
    return sum;
}
 
2..5 each { |base|
    var seq = (0..9 map {|i| vdc([i], base) });
    "base %d: %s\n".printf(base, seq.map{|n| "%.4f" % n}.join(', '));
}
```

#### Output:
```
base 2: 0.0000, 0.5000, 0.2500, 0.7500, 0.1250, 0.6250, 0.3750, 0.8750, 0.0625, 0.5625
base 3: 0.0000, 0.3333, 0.6667, 0.1111, 0.4444, 0.7778, 0.2222, 0.5556, 0.8889, 0.0370
base 4: 0.0000, 0.2500, 0.5000, 0.7500, 0.0625, 0.3125, 0.5625, 0.8125, 0.1250, 0.3750
base 5: 0.0000, 0.2000, 0.4000, 0.6000, 0.8000, 0.0400, 0.2400, 0.4400, 0.6400, 0.8400
```