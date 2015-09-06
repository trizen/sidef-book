[1]: http://rosettacode.org/wiki/Magic_squares_of_odd_order

# [Magic squares of odd order][1]

```ruby
__USE_INTNUM__
 
func magic_square(n) {
 
    (n % 2 == 0) || (n < 0) && (
        warn "Sorry, must be a positive odd integer.";
        return;
    );
 
    var x = int(n/2);
    var y = 0;
    var i = 1;
    var sq = n.of { n.of(0) };
 
    range(0, n*n - 1).each {
        sq[(i % n ? y-- : y++) % n][(i % n ? x++ : x) % n] = i++;
    }
 
    return sq;
}
 
func print_square(sq) {
    var f = "%#{(sq.len**2).len}d";
    sq.each {|row|
        say row.map{ f % _ }.join(' ');
    };
}
 
var(n=5) = ARGV.map{.to_i}...;
var sq = magic_square(n);
print_square(sq);
 
say "\nThe magic number is: #{sq[0].sum}";
```

#### Output:
```
17 24  1  8 15
23  5  7 14 16
 4  6 13 20 22
10 12 19 21  3
11 18 25  2  9

The magic number is: 65
```