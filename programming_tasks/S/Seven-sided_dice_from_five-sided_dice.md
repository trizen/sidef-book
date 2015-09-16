[1]: http://rosettacode.org/wiki/Seven-sided_dice_from_five-sided_dice

# [Seven-sided dice from five-sided dice][1]

```ruby
func dice5 { 1 + 5.rand.int }
 
func dice7 {
  loop {
    var d7 = ((5*dice5() + dice5() - 6) % 8);
    d7 && return d7;
  }
}
 
var count7 = Hash.new;
count7.default(0);
 
var n = 1e6;
n.times { count7[dice7()]++ };
count7.keys.sort.each { |k|
    printf("%s: %5.2f%%\n", k, 100*(count7[k]/n * 7 - 1));
};
```

#### Output:
```
1: -0.00%
2:  0.02%
3:  0.23%
4:  0.42%
5: -0.23%
6: -0.54%
7:  0.10%
```