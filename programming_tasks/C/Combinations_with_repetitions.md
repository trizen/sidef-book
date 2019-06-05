[1]: https://rosettacode.org/wiki/Combinations_with_repetitions

# [Combinations with repetitions][1]

```ruby
func cwr (n, l, a = []) {
    n>0 ? (^l -> map {|k| __FUNC__(n-1, l.slice(k), [a..., l[k]]) }) : a
}

cwr(2, %w(iced jam plain)).each {|a|
    say a.map{ .join(' ') }.join("\n")
}
```

Also built-in:

```ruby
%w(iced jam plain).combinations_with_repetition(2, {|*a|
    say a.join(' ')
})
```

#### Output:
```
iced iced
iced jam
iced plain
jam jam
jam plain
plain plain
```

Efficient counting of the total number of combinations with repetition:

```ruby
func cwr_count (n, m) { binomial(n + m - 1, m) }
printf("\nThere are %s ways to pick 7 out of 10 with repetition\n", cwr_count(10, 7))
```

#### Output:
```
There are 11440 ways to pick 7 out of 10 with repetition
```
