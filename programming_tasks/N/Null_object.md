[1]: https://rosettacode.org/wiki/Null_object

# [Null object][1]

The absence of a value is represented by _nil_

```ruby
var undefined          # initialized with an implicit nil
say undefined==nil     # true
say defined(nil)       # false
```


However, _nil_ is not an object, so we can't call methods on it. Alternatively, Sidef provides the _null_ object:

```ruby
var null_obj = null         # initialize with a null value
say null_obj.is_a(null)     # true
say defined(null_obj)       # true
```
