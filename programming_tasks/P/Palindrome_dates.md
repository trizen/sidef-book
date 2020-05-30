[1]: https://rosettacode.org/wiki/Palindrome_dates

# [Palindrome dates][1]

```ruby
var palindates = Enumerator({ |f|
    var d = Date.strptime("2020-02-02", "%Y-%m-%d")
    loop {
        f(d) if d.strftime("%Y%m%d").is_palindrome
        d.add_days!(1)
    }
})

palindates.first(15).each { .strftime("%Y-%m-%d").say }
```

#### Output:
```
2020-02-02
2021-12-02
2030-03-02
2040-04-02
2050-05-02
2060-06-02
2070-07-02
2080-08-02
2090-09-02
2101-10-12
2110-01-12
2111-11-12
2120-02-12
2121-12-12
2130-03-12
```

Faster approach:

```ruby
var palindates = gather {
    for y in (2020 .. 9999) {
        var (m, d) = Str(y).flip.last(4).split(2)...
        with ([y,m,d].join('-')) {|t|
            take(t) if Date.valid(t, "%Y-%m-%d")
        }
    }
}

say "Count of palindromic dates [2020..9999]: #{palindates.len}"

for a,b in ([
    ["First 15:", palindates.head(15)],
    ["Last 15:",  palindates.tail(15)]
]) {
    say ("\n#{a}\n", b.slices(5).map { .join("   ") }.join("\n"))
}
```

#### Output:

```
Count of palindromic dates [2020..9999]: 285

First 15:
2020-02-02   2021-12-02   2030-03-02   2040-04-02   2050-05-02
2060-06-02   2070-07-02   2080-08-02   2090-09-02   2101-10-12
2110-01-12   2111-11-12   2120-02-12   2121-12-12   2130-03-12

Last 15:
9170-07-19   9180-08-19   9190-09-19   9201-10-29   9210-01-29
9211-11-29   9220-02-29   9221-12-29   9230-03-29   9240-04-29
9250-05-29   9260-06-29   9270-07-29   9280-08-29   9290-09-29
```
