[1]: https://rosettacode.org/wiki/Arithmetic_evaluation

# [Arithmetic evaluation][1]

```ruby
func evalArithmeticExp(s) {

    func evalExp(s) {

        func operate(s, op) {
           s.split(op).map{|c| Number(c) }.reduce(op)
        }

        func add(s) {
            operate(s.sub(/^\+/,'').sub(/\++/,'+'), '+')
        }

        func subtract(s) {
            s.gsub!(/(\+-|-\+)/,'-')

            if (s ~~ /--/) {
                return(add(s.sub(/--/,'+')))
            }

            var b = s.split('-')
            b.len == 3 ? (-1*Number(b[1]) - Number(b[2]))
                       : operate(s, '-')
        }

        s.gsub!(/[()]/,'').gsub!(/-\+/, '-')

        var reM  = /\*/
        var reMD = %r"(\d+\.?\d*\s*[*/]\s*[+-]?\d+\.?\d*)"

        var reA  = /\d\+/
        var reAS = /(-?\d+\.?\d*\s*[+-]\s*[+-]?\d+\.?\d*)/

        while (var match = reMD.match(s)) {
            match[0] ~~ reM
                ? s.sub!(reMD, operate(match[0], '*').to_s)
                : s.sub!(reMD, operate(match[0], '/').to_s)
        }

        while (var match = reAS.match(s)) {
            match[0] ~~ reA
                ? s.sub!(reAS,      add(match[0]).to_s)
                : s.sub!(reAS, subtract(match[0]).to_s)
        }

        return s
    }

    var rePara = /(\([^\(\)]*\))/
    s.split!.join!('').sub!(/^\+/,'')

    while (var match = s.match(rePara)) {
        s.sub!(rePara, evalExp(match[0]))
    }

    return Number(evalExp(s))
}
```


Testing the function:

```ruby
for expr,res in [
     ['2+3'                                      =>        5],
     ['-4-3'                                     =>       -7],
     ['-+2+3/4'                                  =>    -1.25],
     ['2*3-4'                                    =>        2],
     ['2*(3+4)+2/4'                              => 2/4 + 14],
     ['2*-3--4+-0.25'                            =>    -2.25],
     ['2 * (3 + (4 * 5 + (6 * 7) * 8) - 9) * 10' =>     7000],
] { 
    var num = evalArithmeticExp(expr)
    assert_eq(num, res)
    "%-45s == %10g\n".printf(expr, num)
}
```
