[1]: http://rosettacode.org/wiki/Averages/Simple_moving_average

# [Averages/Simple moving average][1]

Closure:

```ruby
func simple_moving_average(period) {
 
    var list = [];
    var sum = 0;
 
    func (number) {
        list.append(number);
        sum += number;
        list.len > period && (
            sum -= list.shift;
        );
        return (sum / list.length);
    }.copy;
}
 
var ma3 = simple_moving_average(3);
var ma5 = simple_moving_average(5);
 
[(1 ..^ 5).to_a..., ( 5 ^.. 1 ).to_a...].reverse -> each {|num|
  printf("Next number = %d, SMA_3 = %.3f, SMA_5 = %.1f\n",
    num, ma3.call(num), ma5.call(num));
}
```


Class:

```ruby
class sma_generator(period) {
 
    def list = [];
    def sum  = 0;
 
    method SMA(number) {
        self.list.append(number);
        self.sum += number;
        self.list.len > self.period && (
            self.sum -= self.list.shift;
        );
        return (self.sum / self.list.len);
    }
}
 
var ma3 = sma_generator(3);
var ma5 = sma_generator(5);
 
[(1 ..^ 5).to_a..., ( 5 ^.. 1 ).to_a...].reverse -> each {|num|
  printf("Next number = %d, SMA_3 = %.3f, SMA_5 = %.1f\n",
    num, ma3.SMA(num), ma5.SMA(num));
}
```