[1]: http://rosettacode.org/wiki/Null_object

# [Null object][1]

The absence of a value is represented by _nil_

```ruby
var undefined;         # initialized with an implicit nil
say undefined==nil;    # true
say defined(nil)       # false
```


However, _nil_ is not an object, so we can't call methods on it. Alternatively, Sidef provides the _Null_ object:

```ruby
var null_obj = Null;        # initialize with a Null value  
say null_obj.is_a(Null);    # true
say defined(null_obj);      # true
```