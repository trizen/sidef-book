[1]: https://rosettacode.org/wiki/Numerical_integration

# [Numerical integration][1]

```ruby
func sum(f, start, from, to) {
    var s = 0
    for i in RangeNum(start, to, from-start) {
        s += f(i)
    }
    return s
}
 
func leftrect(f, a, b, n) {
    var h = ((b - a) / n)
    h * sum(f, a, a+h, b-h)
}
 
func rightrect(f, a, b, n) {
    var h = ((b - a) / n)
    h * sum(f, a+h, a + 2*h, b)
}
 
func midrect(f, a, b, n) {
    var h = ((b - a) / n)
    h * sum(f, a + h/2, a + h + h/2, b - h/2)
}
 
func trapez(f, a, b, n) {
    var h = ((b - a) / n)
    h/2 * (f(a) + f(b) + sum({ f(_)*2 }, a+h, a + 2*h, b-h))
}
 
func simpsons(f, a, b, n) {
    var h = ((b - a) / n)
    var h2 = h/2
 
    var sum1 = f(a + h2)
    var sum2 = 0
 
    sum({|i| sum1 += f(i + h2); sum2 += f(i); 0 }, a+h, a+h+h, b-h)
    h/6 * (f(a) + f(b) + 4*sum1 + 2*sum2)
}
 
func tryem(label, f, a, b, n, exact) {
    say "\n#{label}\n   in [#{a}..#{b}] / #{n}"
 
    say('              exact result: ', exact)
    say('     rectangle method left: ', leftrect(f, a, b, n))
    say('    rectangle method right: ', rightrect(f, a, b, n))
    say('      rectangle method mid: ', midrect(f, a, b, n))
    say('composite trapezoidal rule: ', trapez(f, a, b, n))
    say('   quadratic simpsons rule: ', simpsons(f, a, b, n))
}
 
tryem('x^3', { _ ** 3 }, 0, 1, 100, 0.25)
tryem('1/x', { 1 / _ }, 1, 100, 1000, log(100))
tryem('x', { _ }, 0, 5_000, 5_000_000, 12_500_000)
tryem('x', { _ }, 0, 6_000, 6_000_000, 18_000_000)
```
