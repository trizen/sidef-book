[1]: http://rosettacode.org/wiki/Roman_numerals/Decode

# [Roman numerals/Decode][1]

```ruby
func roman2arabic(roman) {
 
    var arabic = 0;
    var last_digit = 1000;
 
    static m = :(
        I =>    1,
        V =>    5,
        X =>   10,
        L =>   50,
        C =>  100,
        D =>  500,
        M => 1000,
    );
 
    roman.uc.split('').map{m[_] \\ 0}.each { |digit|
        last_digit < digit && (
            arabic -= (2 * last_digit);
        );
        arabic += (last_digit = digit);
    };
 
    return arabic;
}
 
%w(MCMXC MMVIII MDCLXVI).each { |roman_digit|
    "%-10s == %d\n".printf(roman_digit, roman2arabic(roman_digit));
};
```

#### Output:
```
MCMXC      == 1990
MMVIII     == 2008
MDCLXVI    == 1666
```


Simpler:

```ruby
func roman2arabic(digit) {
    digit.uc.trans([
        M:  '1000+',
        CM:  '900+',
        D:   '500+',
        CD:  '400+',
        C:   '100+',
        XC:   '90+',
        L:    '50+',
        XL:   '40+',
        X:    '10+',
        IX:    '9+',
        V:     '5+',
        IV:    '4+',
        I:     '1+',
    ]).split('+').map{.to_i}.sum;
}
 
%w(MCMXC MMVIII MDCLXVI).each { |roman_num|
    say "#{roman_num}\t-> #{roman2arabic(roman_num)}";
}
```

#### Output:
```
MCMXC   -> 1990
MMVIII  -> 2008
MDCLXVI -> 1666
```
