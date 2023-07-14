[1]: https://rosettacode.org/wiki/Averages/Simple_moving_average

# [Averages/Simple moving average][1]

Implemented with closures:

```ruby
func simple_moving_average(period) {
 
    var list = []
    var sum = 0
 
    func (number) {
        list.append(number)
        sum += number
        if (list.len > period) {
            sum -= list.shift
        }
        (sum / list.length)
    }
}
 
var ma3 = simple_moving_average(3)
var ma5 = simple_moving_average(5)
 
for num (1..5, flip(1..5)) {
  printf("Next number = %d, SMA_3 = %.3f, SMA_5 = %.1f\n",
    num, ma3.call(num), ma5.call(num))
}
```


Implemented as a class:

```ruby
class sma_generator(period, list=[], sum=0) {
 
    method SMA(number) {
        list.append(number)
        sum += number
        if (list.len > period) {
            sum -= list.shift
        }
        (sum / list.len)
    }
}
 
var ma3 = sma_generator(3)
var ma5 = sma_generator(5)
 
for num (1..5, flip(1..5)) {
  printf("Next number = %d, SMA_3 = %.3f, SMA_5 = %.1f\n",
    num, ma3.SMA(num), ma5.SMA(num))
}
```

#### Output:
```
Next number = 1, SMA_3 = 1.000, SMA_5 = 1.0
Next number = 2, SMA_3 = 1.500, SMA_5 = 1.5
Next number = 3, SMA_3 = 2.000, SMA_5 = 2.0
Next number = 4, SMA_3 = 3.000, SMA_5 = 2.5
Next number = 5, SMA_3 = 4.000, SMA_5 = 3.0
Next number = 5, SMA_3 = 4.667, SMA_5 = 3.8
Next number = 4, SMA_3 = 4.667, SMA_5 = 4.2
Next number = 3, SMA_3 = 4.000, SMA_5 = 4.2
Next number = 2, SMA_3 = 3.000, SMA_5 = 3.8
Next number = 1, SMA_3 = 2.000, SMA_5 = 3.0
```
