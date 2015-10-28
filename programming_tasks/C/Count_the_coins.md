[1]: http://rosettacode.org/wiki/Count_the_coins

# [Count the coins][1]

```ruby
var (COINS, CACHE);
 
func do_count(n, m) {
    (n < 0) || (m < 0)
        ? 0
        : (CACHE[n][m] \\= (do_count(n-COINS[m], m) + do_count(n, m-1)));
}
 
func make_change(amount, coins) {
    CACHE = amount.inc.of { |i| coins.size.of { i == 1 ? 1 : nil }};
    COINS = coins;
    do_count(amount, coins.end);
}
 
say make_change(   1_00, [1,5,10,25]);
say make_change(1000_00, [1,5,10,25,50,100]);
```

#### Output:
```
242
13398445413854501
```