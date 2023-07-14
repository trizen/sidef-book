[1]: https://rosettacode.org/wiki/Arithmetic_coding/As_a_generalized_change_of_radix

# [Arithmetic coding/As a generalized change of radix][1]

```ruby
func cumulative_freq(freq) {
    var cf = Hash()
    var total = 0
    256.range.each { |b|
        if (freq.contains(b)) {
            cf{b} = total
            total += freq{b}
        }
    }
    return cf
}

func arithmethic_coding(bytes, radix=10) {

    # The frequency characters
    var freq = Hash()
    bytes.each { |b| freq{b} := 0 ++ }

    # The cumulative frequency table
    var cf = cumulative_freq(freq)

    # Base
    var base = bytes.len

    # Lower bound
    var L = 0

    # Product of all frequencies
    var pf = 1

    # Each term is multiplied by the product of the
    # frequencies of all previously occurring symbols
    bytes.each { |b|
        var x = cf{b}
        L *= base += x*pf
        pf *= freq{b}
    }

    # Upper bound
    var U = L+pf

    var pow = pf.log(radix).int
    var enc = ((U-1) // radix**pow)

    return (enc, pow, freq)
}

func arithmethic_decoding(enc, radix, pow, freq) {

    # Multiply enc by radix^pow
    enc *= radix**pow;

    var base = 0
    freq.each_value { |v| base += v }

    # Create the cumulative frequency table
    var cf = cumulative_freq(freq);

    # Create the dictionary
    var dict = Hash()
    cf.each_kv { |k,v|
        dict{v} = k
    }

    # Fill the gaps in the dictionary
    var lchar = ''
    base.range.each { |i|
        if (dict.contains(i)) {
            lchar = dict{i}
        }
        elsif (!lchar.is_empty) {
            dict{i} = lchar
        }
    }

    # Decode the input number
    var decoded = []
    base.range.reverse.each { |i|

        var pow = base**i;
        var div = enc//pow

        var c  = dict{div}
        var fv = freq{c}
        var cv = cf{c}

        var rem = ((enc - pow*cv) // fv)

        enc = rem
        decoded << c
    }

    # Return the decoded output
    return decoded
}

var radix = 10;      # can be any integer greater or equal with 2

%w(DABDDB DABDDBBDDBA ABRACADABRA TOBEORNOTTOBEORTOBEORNOT).each { |str|

    var (enc, pow, freq) = arithmethic_coding(str.bytes, radix)
    var dec = arithmethic_decoding(enc, radix, pow, freq).join_bytes('UTF-8')

    printf("%-25s=> %19s * %d^%s\n", str, enc, radix, pow);

    if (str != dec) {
        die "\tHowever that is incorrect!"
    }
}
```

#### Output:
```
DABDDB                   =>                 251 * 10^2
DABDDBBDDBA              =>              167351 * 10^6
ABRACADABRA              =>             7954170 * 10^4
TOBEORNOTTOBEORTOBEORNOT => 1150764267498783364 * 10^15
```
