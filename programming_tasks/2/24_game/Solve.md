[1]: http://rosettacode.org/wiki/24_game/Solve

# [24 game/Solve][1]

*With evaluation:*

```ruby
var formats = [
    '((%d %s %d) %s %d) %s %d',
    '(%d %s (%d %s %d)) %s %d',
    '(%d %s %d) %s (%d %s %d)',
    '%d %s ((%d %s %d) %s %d)',
    '%d %s (%d %s (%d %s %d))',
]
 
var op = %w( + - * / )
var operators = op.map { |a| op.map {|b| op.map {|c| "#{a} #{b} #{c}" } } }.flat
 
loop {
    var input = read("Enter four integers or 'q' to exit: ", String)
    input == 'q' && break
 
    if (input !~ /^\h*[1-9]\h+[1-9]\h+[1-9]\h+[1-9]\h*$/) {
        say "Invalid input!"
        next
    }
 
    var n = input.split.map{.to_n}
    var numbers = n.permutations
 
    formats.each { |format|
        numbers.each { |n|
            operators.each { |operator|
                var o = operator.split;
                var str = (format % (n[0],o[0],n[1],o[1],n[2],o[2],n[3]))
                eval(str) == 24 && say str
            }
        }
    }
}
```


*Without evaluation:*

```ruby
var formats = [
    {|a,b,c|
        Hash(
            func   => {|d,e,f,g| ((d.$a(e)).$b(f)).$c(g) },
            format => "((%d #{a} %d) #{b} %d) #{c} %d"
        )
    },
    {|a,b,c|
        Hash(
            func   => {|d,e,f,g| (d.$a((e.$b(f)))).$c(g) },
            format => "(%d #{a} (%d #{b} %d)) #{c} %d",
        )
    },
    {|a,b,c|
        Hash(
            func   => {|d,e,f,g| (d.$a(e)).$b(f.$c(g)) },
            format => "(%d #{a} %d) #{b} (%d #{c} %d)",
        )
    },
    {|a,b,c|
        Hash(
            func   => {|d,e,f,g| (d.$a(e)).$b(f.$c(g)) },
            format => "(%d #{a} %d) #{b} (%d #{c} %d)",
        )
    },
    {|a,b,c|
        Hash(
            func   => {|d,e,f,g| d.$a(e.$b(f.$c(g))) },
            format => "%d #{a} (%d #{b} (%d #{c} %d))",
        )
    },
];
 
var op = %w( + - * / )
var blocks = op.map { |a| op.map { |b| op.map { |c| formats.map { |format|
    format(a,b,c)
}}}}.flat
 
loop {
    var input = Sys.scanln("Enter four integers or 'q' to exit: ");
    input == 'q' && break;
 
    if (input !~ /^\h*[1-9]\h+[1-9]\h+[1-9]\h+[1-9]\h*$/) {
        say "Invalid input!"
        next
    }
 
    var n = input.split.map{.to_n}
    var numbers = n.permutations
 
    blocks.each { |block|
        numbers.each { |n|
            if (block{:func}.call(n...) == 24) {
                say (block{:format} % (n...))
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
