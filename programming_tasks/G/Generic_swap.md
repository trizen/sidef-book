[1]: http://rosettacode.org/wiki/Generic_swap

# [Generic swap][1]

```ruby
func swap(a is Ref, b is Ref) {
    var tmp = *a;
    *a = *b;
    *b = tmp;
}
```


or:

```ruby
func swap(a is Ref, b is Ref) {
    (*a, *b) = (*b, *a);
}
```


or:

```ruby
func swap(a is Ref, b is Ref) {
    [*a, *b] » (b, a);
}
```


The swap functions must be called with variable references.

```ruby
var (x, y) = (1, 2);
swap(\x, \y);
```