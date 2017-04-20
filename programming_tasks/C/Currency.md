[1]: http://rosettacode.org/wiki/Currency

# [Currency][1]

```ruby
struct Item {
    name, price, quant
}
 
var check = %q{
    Hamburger   5.50    4000000000000000
    Milkshake   2.86    2
}.lines.grep(/\S/).map { Item(.words...) }
 
var tax_rate = 0.0765
var fmt = "%-10s %8s %18s %22s\n"
 
printf(fmt, %w(Item Price Quantity Extension)...)
 
var subtotal = check.map { |item|
    var extension = Num(item.price)*Num(item.quant)
    printf(fmt, item.name, item.price, item.quant, extension.round(-2))
    extension
}.sum
 
printf(fmt, '', '', '', '-----------------')
printf(fmt, '', '', 'Subtotal ', subtotal)
 
var tax = (subtotal * tax_rate -> round(-2))
printf(fmt, '', '', 'Tax ', tax)
 
var total = subtotal+tax
printf(fmt, '', '', 'Total ', total)
```

#### Output:
```
Item          Price           Quantity              Extension
Hamburger      5.50   4000000000000000      22000000000000000
Milkshake      2.86                  2                   5.72
                                            -----------------
                             Subtotal    22000000000000005.72
                                  Tax     1683000000000000.44
                                Total    23683000000000006.16
```
