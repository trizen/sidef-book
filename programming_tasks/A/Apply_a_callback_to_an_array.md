[1]: http://rosettacode.org/wiki/Apply_a_callback_to_an_array

# [Apply a callback to an array][1]

Defining a callback function:

```ruby
func callback(i) { say i**2 }
```

The function will get called for each element:

```ruby
[1,2,3,4].each(callback);
```

Same as above, but with the function inlined:

```ruby
[1,2,3,4].each{|i| say i**2 }
```

For creating a new array, we can use the `Array.map` method:

```ruby
[1,2,3,4,5].map{|i| i**2 }
```
