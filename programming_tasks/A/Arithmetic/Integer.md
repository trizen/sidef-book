[1]: http://rosettacode.org/wiki/Arithmetic/Integer

# [Arithmetic/Integer][1]

```ruby
var a = Sys.scanln("First number: ").to_i;
var b = Sys.scanln("Second number: ").to_i;
 
%w'+ - * // % ** ^ | & << >>'.each { |op|
    "#{a} #{op} #{b} = #{a.$op(b)}".say;
}
```

#### Output:
```
First number: 1234
Second number: 7
1234 + 7 = 1241
1234 - 7 = 1227
1234 * 7 = 8638
1234 // 7 = 176
1234 % 7 = 2
1234 ** 7 = 4357186184021382204544
1234 ^ 7 = 1237
1234 | 7 = 1239
1234 & 7 = 2
1234 << 7 = 157952
1234 >> 7 = 9
```
