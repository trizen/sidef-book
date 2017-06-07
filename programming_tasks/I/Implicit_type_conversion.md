[1]: https://rosettacode.org/wiki/Implicit_type_conversion

# [Implicit type conversion][1]

Since version 3.00, all the number types (int, rat, float and complex) are unified in the *Number* class and all the needed conversions are done implicitly. Methods from other classes also make implicit conversions where possible.

```ruby
> 1+"2"            #=> 3
> "1"+2            #=> 12
> sqrt(-4)         #=> 2i
> ("a" + [1,2])    #=> a[1,2]
> ('ha' * '3')     #=> hahaha
> ('ha' * true)    #=> ha
```