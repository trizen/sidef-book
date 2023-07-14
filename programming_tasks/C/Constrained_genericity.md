[1]: https://rosettacode.org/wiki/Constrained_genericity

# [Constrained genericity][1]

```ruby
class FoodBox(*food { .all { .respond_to(:eat) } }) { }
 
class Fruit { method eat { ... } }
class Apple < Fruit {  }
 
say FoodBox(Fruit(), Apple()).dump  #=> FoodBox(food: [Fruit(), Apple()])
say FoodBox(Apple(), "foo")         #!> ERROR: class `FoodBox` !~ (Apple, String)
```