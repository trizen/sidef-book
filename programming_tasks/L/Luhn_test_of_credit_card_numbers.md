[1]: http://rosettacode.org/wiki/Luhn_test_of_credit_card_numbers

# [Luhn test of credit card numbers][1]

```ruby
func luhn (n) {
    var chars = n.to_s.reverse.split(1);
    var (i, sum) = (0, 0);
    static a = (0..9 map {|j| (2*j / 10 int) + (2*j % 10 int) });
    chars.each { |j|
        sum += (i++ is_odd ? a[j] : j);
    };
    return (sum % 10 == 0);
}
 
# Test and display
[49927398716, 49927398717, 1234567812345678, 1234567812345670].each { |n|
    say [n, luhn(n)].dump;
}
```

#### Output:
```
[49927398716, true]
[49927398717, false]
[1234567812345678, false]
[1234567812345670, true]
```