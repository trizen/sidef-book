[1]: http://rosettacode.org/wiki/Evaluate_binomial_coefficients

# [Evaluate binomial coefficients][1]

Straightforward translation of the formula:

```ruby
__USE_INTNUM__
 
func binomial(n,k) {
    n! / ((n-k)! * k!);
}
 
say binomial(400, 200);
```


Alternatively, by using the _Number.nok()_ method:

```ruby
say 400.nok(200);
```