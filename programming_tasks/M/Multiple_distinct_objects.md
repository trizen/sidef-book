[1]: http://rosettacode.org/wiki/Multiple_distinct_objects

# [Multiple distinct objects][1]

```ruby
[Foo.new] * n       # incorrect (only one distinct object is created)
```
```ruby
n.of {Foo.new}      # correct
```
