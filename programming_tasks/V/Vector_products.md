[1]: https://rosettacode.org/wiki/Vector_products

# [Vector products][1]

```ruby
class MyVector(x, y, z) {
    method ∙(vec) {
        [self{:x,:y,:z}] »*« [vec{:x,:y,:z}] «+»
    }
 
    method ⨉(vec) {
        MyVector(self.y*vec.z - self.z*vec.y,
               self.z*vec.x - self.x*vec.z,
               self.x*vec.y - self.y*vec.x)
    }
 
    method to_s {
        "(#{x}, #{y}, #{z})"
    }
}
 
var a = MyVector(3, 4, 5)
var b = MyVector(4, 3, 5)
var c = MyVector(-5, -12, -13)
 
say "a=#{a}; b=#{b}; c=#{c};"
say "a ∙ b = #{a ∙ b}"
say "a ⨉ b = #{a ⨉ b}"
say "a ∙ (b ⨉ c) = #{a ∙ (b ⨉ c)}"
say "a ⨉ (b ⨉ c) = #{a ⨉ (b ⨉ c)}"
```

#### Output:
```
a=(3, 4, 5); b=(4, 3, 5); c=(-5, -12, -13);
a ∙ b = 49
a ⨉ b = (5, 5, -7)
a ∙ (b ⨉ c) = 6
a ⨉ (b ⨉ c) = (-267, 204, -3)
```
