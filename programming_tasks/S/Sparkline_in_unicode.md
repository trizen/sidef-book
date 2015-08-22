[1]: http://rosettacode.org/wiki/Sparkline_in_unicode

# [Sparkline in unicode][1]

```ruby
var bar = '▁'..'█';
loop {
    print 'Numbers, please, separated by space/commas: ';
    var numbers = read(String).trim.split(/[\s,]+/).map{.to_f};
    var (min, max) = numbers.minmax;
    say "min: %5f; max: %5f"%[min, max];
    var div = ((max - min) / bar.offset);
    say (min == max ? bar.last*numbers.len : numbers.map{|num| bar[(num - min) / div]}.join);
};
```

#### Output:
```
Numbers, please, separated by space/commas: 1 2 3 4 5 6 7 8 7 6 5 4 3 2 1
min: 1.000000; max: 8.000000
▁▂▃▄▅▆▇█▇▆▅▄▃▂▁
Numbers, please, separated by space/commas: 1.5, 0.5 3.5, 2.5 5.5, 4.5 7.5, 6.5
min: 0.500000; max: 7.500000
▂▁▄▃▆▅█▇
```
