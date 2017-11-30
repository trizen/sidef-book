[1]: http://rosettacode.org/wiki/Luhn_test_of_credit_card_numbers

# [Luhn test of credit card numbers][1]

```ruby
func luhn (n) {
    var chars = n.digits
    var (i, sum) = (0, 0)
    static a = {|j| (2*j // 10) + (2*j % 10) }.map(^10)
    for j (chars) {
        sum += (i++.is_odd ? a[j] : j)
    }
    return (sum % 10 == 0)
}
 
# Test and display
for n in [49927398716, 49927398717, 1234567812345678, 1234567812345670] {
    say [n, luhn(n)]
}
```

#### Output:
```
[49927398716, true]
[49927398717, false]
[1234567812345678, false]
[1234567812345670, true]
```
