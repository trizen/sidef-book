[1]: http://rosettacode.org/wiki/Sequence_of_primes_by_Trial_Division

# [Sequence of primes by Trial Division][1]

Using the _is_prime()_ function from: ["Primality by trial division"](http://rosettacode.org/wiki/Primality_by_trial_division#Sidef)

```ruby
func prime_seq(amount, callback) {
    var (counter, number) = (0, 0);
    while (counter < amount) {
        if (is_prime(number)) {
            callback(number);
            counter += 1;
        };
        number += 1;
    };
};
 
prime_seq(100, {|p| say p});     # prints the first 100 primes
```