[1]: http://rosettacode.org/wiki/Arithmetic/Integer

# [Arithmetic/Integer][1]

```ruby
var a = Sys.scanln("First number: ").to_i;
var b = Sys.scanln("Second number: ").to_i;
 
%w'+ - * / % ** ^ | & << >>'.each { |op|
    "#{a} #{op} #{b} = #{a.$op(b)}".say;
}
```


*Output:*


#### Output:
```
** Integer a: 100
** Integer b: 20
100 + 20 = 120
100 - 20 = 80
100 * 20 = 2000
100 / 20 = 5
100 % 20 = 0
100 ** 20 = 10000000000000000000000000000000000000000
100 ^ 20 = 112
100 | 20 = 116
100 & 20 = 4
100 << 20 = 104857600
100 >> 20 = 0
```