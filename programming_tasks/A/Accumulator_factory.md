[1]: http://rosettacode.org/wiki/Accumulator_factory

# [Accumulator factory][1]

```ruby
class Accumulator(sum) {
    method add(num) {
        sum += num;
    }
}
 
var x = Accumulator(1);
x.add(5);
Accumulator(3);
say x.add(2.3);               # prints: 8.3
```


The same thing can be achieved by returning a closure from the *Accumulator* function.

```ruby
func Accumulator(sum) {
    func(num) { sum += num };
}
 
var x = Accumulator(1);
x(5);
Accumulator(3);
say x(2.3);                  # prints: 8.3
```