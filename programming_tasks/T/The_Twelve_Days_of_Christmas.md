[1]: https://rosettacode.org/wiki/The_Twelve_Days_of_Christmas

# [The Twelve Days of Christmas][1]

```ruby
var days = <first second third fourth fifth sixth seventh eighth ninth tenth eleventh twelfth>
 
var gifts = <<'EOT'.lines
  And a partridge in a pear tree.
  Two turtle doves,
  Three french hens,
  Four calling birds,
  Five golden rings,
  Six geese a-laying,
  Seven swans a-swimming,
  Eight maids a-milking,
  Nine ladies dancing,
  Ten lords a-leaping,
  Eleven pipers piping,
  Twelve drummers drumming,
EOT
 
func nth(n) { say "On the #{days[n]} day of Christmas, my true love gave to me:" }
 
nth(0)
say gifts[0].sub('And a', 'A')
 
for d (1..11) {
    say ''
    nth(d)
    for i flip(0..d) {
        say gifts[i]
    }
}
```

#### Output:
```
On the first day of Christmas, my true love gave to me:
  A partridge in a pear tree.

On the second day of Christmas, my true love gave to me:
  Two turtle doves,
  And a partridge in a pear tree.

On the third day of Christmas, my true love gave to me:
  Three french hens,
  Two turtle doves,
  And a partridge in a pear tree.

On the fourth day of Christmas, my true love gave to me:
  Four calling birds,
  Three french hens,
  Two turtle doves,
  And a partridge in a pear tree.
.
.
.
On the twelfth day of Christmas, my true love gave to me:
  Twelve drummers drumming,
  Eleven pipers piping,
  Ten lords a-leaping,
  Nine ladies dancing,
  Eight maids a-milking,
  Seven swans a-swimming,
  Six geese a-laying,
  Five golden rings,
  Four calling birds,
  Three french hens,
  Two turtle doves,
  And a partridge in a pear tree.
```
