[1]: https://rosettacode.org/wiki/Four_is_magic

# [Four is magic][1]

```ruby
func cardinal(n) {
    static lingua_en = frequire("Lingua::EN::Numbers")
    lingua_en.num2en(n) - / and|,/g
}
 
func four_is_magic(n) {
    var str = ""
    loop {
       str += (cardinal(n) + " is ")
       if (n == 4) {
           str += "magic."
           break
       } else {
           n = cardinal(n).len
           str += (cardinal(n) + ", ")
       }
   }
   str.tc
}
 
[0, 4, 6, 11, 13, 75, 337, -164, 9_876_543_209].each { |n|
    say four_is_magic(n)
}
```

#### Output:
```
Zero is four, four is magic.
Four is magic.
Six is three, three is five, five is four, four is magic.
Eleven is six, six is three, three is five, five is four, four is magic.
Thirteen is eight, eight is five, five is four, four is magic.
Seventy-five is twelve, twelve is six, six is three, three is five, five is four, four is magic.
Three hundred thirty-seven is twenty-six, twenty-six is ten, ten is three, three is five, five is four, four is magic.
Negative one hundred sixty-four is thirty-one, thirty-one is ten, ten is three, three is five, five is four, four is magic.
Nine billion eight hundred seventy-six million five hundred forty-three thousand two hundred nine is ninety-seven, ninety-seven is twelve, twelve is six, six is three, three is five, five is four, four is magic.
```
