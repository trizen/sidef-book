[1]: http://rosettacode.org/wiki/24_game/Solve

# [24 game/Solve][1]

```ruby
var formats = [
    '((%d %s %d) %s %d) %s %d',
    '(%d %s (%d %s %d)) %s %d',
    '(%d %s %d) %s (%d %s %d)',
    '%d %s ((%d %s %d) %s %d)',
    '%d %s (%d %s (%d %s %d))',
];

var op = %w( + - * / );
var operators = op.map { |a| op.map {|b| op.map {|c| "#{a} #{b} #{c}" } } }.flatten;

loop {
    var input = Sys.scanln("Enter four integers or 'q' to exit: ");
    input == 'q' && break;

    input ~~ /^\h*[1-9]\h+[1-9]\h+[1-9]\h+[1-9]\h*$/ || (
        say "Invalid input!"; next;
    );

    var n = input.split.map{.to_i};
    var numbers = n.permute;

    formats.each { |format|
        numbers.each { |n|
            operators.each { |operator|
                var o = operator.split;
                var str = (format % (n[0],o[0],n[1],o[1],n[2],o[2],n[3]));
                eval(str) == 24 && say str;
            }
        }
    }
}
```

#### Output:
```
Enter four integers or 'q' to exit: 8 7 9 6
(8 / (9 - 7)) * 6
(6 / (9 - 7)) * 8
(8 * 6) / (9 - 7)
(6 * 8) / (9 - 7)
8 / ((9 - 7) / 6)
6 / ((9 - 7) / 8)
8 * (6 / (9 - 7))
6 * (8 / (9 - 7))
Enter four integers or 'q' to exit: q
```
