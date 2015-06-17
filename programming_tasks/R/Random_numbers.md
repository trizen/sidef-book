[1]: http://rosettacode.org/wiki/Random_numbers

# [Random numbers][1]

```ruby
1000.of { 1 + (0.5 * Math.sqrt(-2 * Math.log(Math.rand)) * Math.cos(2 * Math::PI * Math.rand)) };
```


or:

```ruby
1000.of { 1 + (0.5 * (-2 * 1.rand.log -> sqrt) * (2 * Math::PI * 1.rand -> cos)) };
```