[1]: http://rosettacode.org/wiki/Probabilistic_choice

# [Probabilistic choice][1]

```ruby
define TRIALS = 1e4;
 
func prob_choice_picker(options) {
    var n = 0;
    var a = [];
    options.each { |k,v|
        n += v;
        a << [n, k];
    };
    closure {
        var r = 1.rand;
        a.first{|e| r <= e[0] }[1];
    };
}
 
var ps = Hash.new(
   aleph  => 1/5,
   beth   => 1/6,
   gimel  => 1/7,
   daleth => 1/8,
   he     => 1/9,
   waw    => 1/10,
   zayin  => 1/11
);
 
ps[:heth] = (1 - ps.values.sum);
 
var picker = prob_choice_picker(ps);
var results = Hash.new -> default(0);
 
range(0, TRIALS).each {
    results[picker()]++;
};
 
say "Event   Occurred  Expected  Difference";
results.sort_by {|k| results[k] }.reverse.each { |pair|
    var(k, v) = pair...;
    printf("%-6s  %f  %f  %f\n",
        k, v/TRIALS, ps[k],
        abs(v/TRIALS - ps[k])
    );
};
```

#### Output:
```
Event   Occurred  Expected  Difference
aleph   0.196300  0.200000  0.003700
beth    0.165600  0.166667  0.001067
gimel   0.143700  0.142857  0.000843
daleth  0.123900  0.125000  0.001100
he      0.111800  0.111111  0.000689
waw     0.101900  0.100000  0.001900
zayin   0.088100  0.090909  0.002809
heth    0.068800  0.063456  0.005344
```