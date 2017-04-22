[1]: http://rosettacode.org/wiki/Long_multiplication

# [Long multiplication][1]

(Note that arbitrary precision arithmetic is native in Sidef).

```ruby
say (2**64 * 2**64);
```
```ruby
func add_with_carry(result, addend, addendpos) {
    loop {
        while (result.len < addendpos+1) {
            result.append(0)
        }
        var addend_digits = (addend.to_i + result[addendpos] -> digits)
        result[addendpos] = addend_digits.pop
        addend_digits.len > 0 || break
        addend = addend_digits.pop
        addendpos++
    }
}
 
func longhand_multiplication(multiplicand, multiplier) {
 
    var result = []
    var multiplicand_offset = 0
 
    multiplicand.reverse.each { |multiplicand_digit|
        var multiplier_offset = multiplicand_offset
        multiplier.reverse.each { |multiplier_digit|
            var multiplication_result = (multiplicand_digit.to_i * multiplier_digit.to_i -> to_s)
 
            var addend_offset = multiplier_offset
            multiplication_result.reverse.each { |result_digit_addend|
                add_with_carry(result, result_digit_addend, addend_offset)
                addend_offset++
            }
            multiplier_offset++
        }
        multiplicand_offset++
    }
 
    return result.join.reverse
}
 
say longhand_multiplication('18446744073709551616', '18446744073709551616')
```


**A faster approach:**

```ruby
func long_multiplication(String a, String b) -> String {

    if (a.len < b.len) {
        (a, b) = (b, a)
    }

    '0' ~~ [a, b] && return '0'

    var x = a.reverse.chars.map{.to_n}
    var y = b.reverse.chars.map{.to_n}

    var xlen = x.end
    var ylen = y.end

    var mem = 0
    var map = y.len.of { [] }

    for j in ^y {
        for i in ^x {
            var n = (x[i]*y[j] + mem)
            var(d, m) = n.divmod(10)
            if (i == xlen) {
                map[j] << (m, d)
                mem = 0;
            }
            else {
                map[j] << m
                mem = d
            }
        }

        var n = (ylen - j)
        n > 0 && map[j].append(n.of(0)...)
        var m = (ylen - n)
        m > 0 && map[j].prepend(m.of(0)...)
    }

    var result = []
    var mrange = ^map
    var end    = (xlen + ylen + 2)

    for i in ^end {
        var n = (mrange.map {|j| map[j][i] }.sum + mem)
        (mem, result[result.end+1]) = n.divmod(10)
    }

    result.join.reverse -= /^0+/
}

say long_multiplication('18446744073709551616', '18446744073709551616')
```

#### Output:
```
340282366920938463463374607431768211456
```
