[1]: http://rosettacode.org/wiki/Look-and-say_sequence

# [Look-and-say sequence][1]

```ruby
func lookandsay(str) {
    str.gsub(/((.)\2*)/, {|a,b| a.len.to_s + b });
}
 
var num = "1";
{
  say num;
  num = lookandsay(num);
} * 10;
```

#### Output:
```
1
11
21
1211
111221
312211
13112221
1113213211
31131211131221
13211311123113112211
```