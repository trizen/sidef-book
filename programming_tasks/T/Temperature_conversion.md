[1]: https://rosettacode.org/wiki/Temperature_conversion

# [Temperature conversion][1]

```ruby
var scale = Hash(
    Celcius    => Hash(factor => 1  , offset => -273.15 ),
    Rankine    => Hash(factor => 1.8, offset =>    0    ),
    Fahrenheit => Hash(factor => 1.8, offset => -459.67 ),
)

var kelvin = read("Enter a temperature in Kelvin: ", Number)
kelvin >= 0 || die "No such temperature!"

scale.keys.sort.each { |key|
    printf("%12s:%8.2f\n", key, kelvin*scale{key}{:factor} + scale{key}{:offset})
}
```

#### Output:
```
Enter a temperature in Kelvin: 256
     Celcius:  -17.15
  Fahrenheit:    1.13
     Rankine:  460.80
```
