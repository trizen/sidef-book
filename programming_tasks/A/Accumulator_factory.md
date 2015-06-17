[1]: http://rosettacode.org/wiki/Accumulator_factory

# [Accumulator factory][1]

```ruby
class Accumulator (sum) {
    method add(num) {
        self.sum += num;
    }
}
 
var x = Accumulator(1);
x.add(5);
Accumulator(3);
say x.add(2.3);               # prints: 8.3
```


The same thing can be achieved by using the *.copy* method on the block returned by the *Accumulator* function.

```ruby
func Accumulator(sum) {
    {|num| sum += num }.copy;
}
 
var x = Accumulator(1);
x.call(5);
Accumulator(3);
say x.call(2.3);            # prints: 8.3
```