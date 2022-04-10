[1]: https://rosettacode.org/wiki/Largest_palindrome_product

# [Largest palindrome product][1]

```ruby
func largest_palindrome_product (n) {
 
    for k in ((10**n - 1) `downto` 10**(n-1)) {
        var t = Num("#{k}#{Str(k).flip}")
 
        t.divisors.each {|d|
            if ((d.len == n) && ((t/d).len == n)) {
                return (d, t/d)
            }
        }
    }
}
 
for n in (2..9) {
    var (a,b) = largest_palindrome_product(n)
    say "Largest palindromic product of two #{n}-digit integers: #{a} * #{b} = #{a*b}"
}
```

#### Output:
```
Largest palindromic product of two 2-digit integers: 91 * 99 = 9009
Largest palindromic product of two 3-digit integers: 913 * 993 = 906609
Largest palindromic product of two 4-digit integers: 9901 * 9999 = 99000099
Largest palindromic product of two 5-digit integers: 99681 * 99979 = 9966006699
Largest palindromic product of two 6-digit integers: 999001 * 999999 = 999000000999
Largest palindromic product of two 7-digit integers: 9997647 * 9998017 = 99956644665999
Largest palindromic product of two 8-digit integers: 99990001 * 99999999 = 9999000000009999
Largest palindromic product of two 9-digit integers: 999920317 * 999980347 = 999900665566009999
```
