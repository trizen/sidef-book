[1]: http://rosettacode.org/wiki/Roman_numerals/Encode

# [Roman numerals/Encode][1]

```ruby
func arabic2roman(num, roman='') {
    const lookup = [M:1000, CM:900, D:500, CD:400, C:100, XC:90, L:50, XL:40, X:10, IX:9, V:5, IV:4, I:1];
    lookup.each { |pair|
        while (num >= pair.second) {
            roman += pair.first;
            num -= pair.second;
        }
    };
    return roman;
};
say("1990 in roman is " + arabic2roman(1990));
say("2008 in roman is " + arabic2roman(2008));
say("1666 in roman is " + arabic2roman(1666));
```

#### Output:
```
1990 in roman is MCMXC
2008 in roman is MMVIII
1666 in roman is MDCLXVI
```