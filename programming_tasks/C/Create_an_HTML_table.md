[1]: http://rosettacode.org/wiki/Create_an_HTML_table

# [Create an HTML table][1]

```ruby
class HTML {
    method _attr(Hash h) {
        h.keys.sort.map {|k| %Q' #{k}="#{h{k}}"' }.join
    }

    method _tag(Hash h, name, value) {
        "<#{name}" + self._attr(h) + '>' + value + "</#{name}>"
    }

    method table(Hash h, *data) { self._tag(h, 'table', data.join) }
    method table(*data)         { self.table(Hash(), data...) }
}

class Table < HTML {
    method th(Hash h, value) { self._tag(h, 'th', value) }
    method th(value)         { self.th(Hash(), value) }

    method tr(Hash h, *rows) { self._tag(h, 'tr', rows.join) }
    method tr(*rows)         { self.tr(Hash(), rows...) }

    method td(Hash h, value) { self._tag(h, 'td', value) }
    method td(value)         { self.td(Hash(), value) }
}

var header = %w(&nbsp; X Y Z)
var rows = 5

var html = HTML()
var table = Table()

say html.table(
    # attributes
    Hash(
        cellspacing => 4,
        style => "text-align:right; border: 1px solid;"
     ),

    # header
    table.tr(header.map{|elem| table.th(elem)}...),

    # rows
    (1..rows).map { |i|
        table.tr(
            table.td(:(align => 'right'), i),
            (header.len - 1).of {
                table.td(Hash(align => 'right'), 10000.irand)
            }...
        )
    }...
)
```


#### Output (tidied afterwards):
```
<table cellspacing="4" style="text-align:right; border: 1px solid;">
<tr><th> </th><th>X</th><th>Y</th><th>Z</th></tr>
<tr>
  <td align="right">1</td>
  <td align="right">2308</td>
  <td align="right">6448</td>
  <td align="right">2614</td>
</tr>
<tr>
  <td align="right">2</td>
  <td align="right">8830</td>
  <td align="right">553</td>
  <td align="right">5647</td>
</tr>
<tr>
  <td align="right">3</td>
  <td align="right">9636</td>
  <td align="right">5922</td>
  <td align="right">6384</td>
</tr>
<tr>
  <td align="right">4</td>
  <td align="right">9122</td>
  <td align="right">4832</td>
  <td align="right">8813</td>
</tr>
<tr>
  <td align="right">5</td>
  <td align="right">3331</td>
  <td align="right">5528</td>
  <td align="right">701</td>
</tr>
</table>
```
