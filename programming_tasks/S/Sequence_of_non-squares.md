[1]: http://rosettacode.org/wiki/Sequence_of_non-squares

# [Sequence of non-squares][1]

```ruby
func nonsqr(n) { 0.5 + n.sqrt -> floor + n };
1..22 -> map {|i| nonsqr(i)}.join(' ').say;
 
{ |i|
  nonsqr(i).sqrt -> is_int && (
     "Found a square in the sequence: #{i}".die;
  );
} * 1e6;
```