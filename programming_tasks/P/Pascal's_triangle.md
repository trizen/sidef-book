[1]: http://rosettacode.org/wiki/Pascal's_triangle

# [Pascal's triangle][1]

```ruby
func pascal(rows) {
    var row = [1];
    { | n|
        say row.join(' ');
        row = [1, 0..(n-2).map {|i| row[i] + row[i+1] }..., 1];
    } * rows;
}
 
pascal(10);
```