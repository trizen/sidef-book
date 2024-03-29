[1]: https://rosettacode.org/wiki/Count_the_coins

# [Count the coins][1]

```ruby
func cc(_)                { 0 }
func cc({ .is_neg  }, *_) { 0 }
func cc({ .is_zero }, *_) { 1 }

func cc(amount, first, *rest) is cached {
    cc(amount, rest...) + cc(amount - first, first, rest...);
}

func cc_optimized(amount, *rest) {
    cc(amount, rest.sort_by{|v| -v }...);
}

var x = cc_optimized(100, 1, 5, 10, 25);
say "Ways to change $1 with common coins: #{x}";

var y = cc_optimized(1000 * 100, 1, 5, 10, 25, 50, 100);
say "Ways to change $1000 with addition of less common coins: #{y}";
```

#### Output:
```
Ways to change $1 with common coins: 242
Ways to change $1000 with addition of less common coins: 13398445413854501
```
