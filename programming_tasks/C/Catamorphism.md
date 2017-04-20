[1]: http://rosettacode.org/wiki/Catamorphism

# [Catamorphism][1]

```ruby
say (1..10 -> reduce('+'))
say (1..10 -> reduce{|a,b| a + b})
```
