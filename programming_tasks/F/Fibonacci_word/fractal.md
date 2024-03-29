[1]: https://rosettacode.org/wiki/Fibonacci_word/fractal

# [Fibonacci word/fractal][1]

```ruby
var(m=17, scale=3) = ARGV.map{.to_i}...

(var world = Hash.new){0}{0} = 1
var loc = 0
var dir = 1i

var fib = ['1', '0']
func fib_word(n) {
    fib[n] \\= (fib_word(n-1) + fib_word(n-2))
}

func step {
    scale.times {
        loc += dir
        world{loc.im}{loc.re} = 1
    }
}

func turn_left  { dir *=  1i }
func turn_right { dir *= -1i }

var n = 1
fib_word(m).each { |c|
    if (c == '0') {
        step()
        n % 2 == 0 ? turn_left()
                   : turn_right()
    } else { n++ }
}

func braille_graphics(a) {
    var (xlo, xhi, ylo, yhi) = ([Inf, -Inf]*2)...

    a.each_key { |y|
        ylo.min!(y.to_i)
        yhi.max!(y.to_i)
        a{y}.each_key { |x|
            xlo.min!(x.to_i)
            xhi.max!(x.to_i)
        }
    }

    for y in (ylo..yhi `by` 4) {
        for x in (xlo..xhi `by` 2) {
            var cell = 0x2800

            a{y+0}{x+0} && (cell += 1)
            a{y+1}{x+0} && (cell += 2)
            a{y+2}{x+0} && (cell += 4)
            a{y+0}{x+1} && (cell += 8)
            a{y+1}{x+1} && (cell += 16)
            a{y+2}{x+1} && (cell += 32)
            a{y+3}{x+0} && (cell += 64)
            a{y+3}{x+1} && (cell += 128)

            print cell.chr
        }
        print "\n"
    }
}

braille_graphics(world)
```

#### Output:
```
$ sidef fib_word_fractal.sf 12 3
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣇⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡤⢤⠀⡤⠼⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢰⠒⠃⠘⠒⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠉⣇⣸⠉⣇⣀⠀⣀⣸⠉⣇⣀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡤⠼⠀⠧⢤⠀⡤⠼⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠓⢲⠀⡖⠚⠀⠓⢲⠀⡖⢲⠀⠀
⠀⠀⠀⠀⢀⣀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢈⣉⡁⠀⠀⠀⢈⣉⡁⢈⣉⡇
⠀⠀⠀⡤⠼⠀⠧⢤⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡤⠼⠀⠧⢤⠀⡤⠼⠀⠧⠼⠀⠀
⠀⠀⠀⠓⢲⠀⡖⠚⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠓⢲⠀⡖⠚⠀⠓⢲⠀⠀⠀⠀⠀
⠉⢹⣀⡏⠉⠀⠉⢹⣀⡏⢹⣀⡀⢀⣀⡏⢹⣀⡏⠉⠀⠉⢹⣀⡏⠉⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⢠⠤⡄⢠⠤⠇⠸⠤⡄⢠⠤⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⡖⠚⠀⠓⠚⠀⠀⠀⠀⠓⠚⠀⠓⢲⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠉⢹⣀⡏⢹⣀⡀⢀⣀⡏⢹⣀⡏⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠤⠇⠸⠤⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⠒⡆⢰⠒⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
```
