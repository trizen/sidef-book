[1]: http://rosettacode.org/wiki/Parsing/Shunting-yard_algorithm

# [Parsing/Shunting-yard algorithm][1]

```ruby
var prec = Hash.new(
    '^' => 4,
    '*' => 3,
    '/' => 3,
    '+' => 2,
    '-' => 2,
    '(' => 1,
);
 
var assoc = Hash.new(
    '^' => 'right',
    '*' => 'left',
    '/' => 'left',
    '+' => 'left',
    '-' => 'left',
);
 
func shunting_yard(prog) {
    var inp = prog.words;
    var ops = [];
    var res = [];
 
    func report (op) { printf("%25s    %-7s %10s %s\n", res.to_s, ops.to_s, op, inp.to_s) };
    func shift  (t)  { report( "shift #{t}"); ops << t };
    func reduce (t)  { report("reduce #{t}"); res << t };
 
    while (inp) {
        given(var t = inp.shift)
           ~ (/\d/) { reduce(t) }
           > ('(')  { shift(t) }
           > (')')  { while (ops && (var x = ops.pop) && (x != '(')) { reduce(x) } }
           : {
                var newprec = prec[t];
                while (ops) {
                    var oldprec = prec[ops[-1]];
                    any {
                        newprec > oldprec;
                        all {
                            newprec == oldprec;
                            assoc[t] == 'right';
                        };
                    } && break;
                    reduce(ops.pop);
                };
                shift(t);
            }
        ;
    };
    while (ops) { reduce(ops.pop) };
    return res;
}
 
say shunting_yard('3 + 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3').to_s;
```

#### Output:
```
                                       reduce 3 + 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3
                        3               shift + 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3
                        3    +         reduce 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3
                      3 4    +          shift * 2 / ( 1 - 5 ) ^ 2 ^ 3
                      3 4    + *       reduce 2 / ( 1 - 5 ) ^ 2 ^ 3
                    3 4 2    +         reduce * ( 1 - 5 ) ^ 2 ^ 3
                  3 4 2 *    +          shift / ( 1 - 5 ) ^ 2 ^ 3
                  3 4 2 *    + /        shift ( 1 - 5 ) ^ 2 ^ 3
                  3 4 2 *    + / (     reduce 1 - 5 ) ^ 2 ^ 3
                3 4 2 * 1    + / (      shift - 5 ) ^ 2 ^ 3
                3 4 2 * 1    + / ( -   reduce 5 ) ^ 2 ^ 3
              3 4 2 * 1 5    + / (     reduce - ^ 2 ^ 3
            3 4 2 * 1 5 -    + /        shift ^ 2 ^ 3
            3 4 2 * 1 5 -    + / ^     reduce 2 ^ 3
          3 4 2 * 1 5 - 2    + / ^      shift ^ 3
          3 4 2 * 1 5 - 2    + / ^ ^   reduce 3
        3 4 2 * 1 5 - 2 3    + / ^     reduce ^
      3 4 2 * 1 5 - 2 3 ^    + /       reduce ^
    3 4 2 * 1 5 - 2 3 ^ ^    +         reduce /
  3 4 2 * 1 5 - 2 3 ^ ^ /              reduce +
3 4 2 * 1 5 - 2 3 ^ ^ / +
```
