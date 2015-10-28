[1]: http://rosettacode.org/wiki/Combinations_with_repetitions

# [Combinations with repetitions][1]

```ruby
func p (n, a, l) { n>0 ? (l.range.map{p(n-1, a+[l[_]], l.ft(_))}) : a };
func f (n)       { n>0 ? (n * f(n - 1)) : 1 };
func n (n, m)    { f(n + m - 1) / f(n) / f(m - 1) };
 
p(2, [], %w(iced jam plain)).each { |a|
    say a.map{|pair| pair.join(" ")}.join("\n");
}
 
printf("\nThere are %d ways to pick 7 out of 10\n", n(7, 10));
```

#### Output:
```
iced iced
iced jam
iced plain
jam jam
jam plain
plain plain

There are 11440 ways to pick 7 out of 10
```