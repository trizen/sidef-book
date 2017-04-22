[1]: http://rosettacode.org/wiki/Subleq

# [Subleq][1]

```ruby
var memory = ARGV.map{.to_i}
var ip = 0
 
while (ip.ge(0) && ip.lt(memory.len)) {
    var (a, b, c) = memory[ip, ip+1, ip+2]
    ip += 3
    if (a < 0) {
        memory[b] = STDIN.getc.ord
    }
    elsif (b < 0) {
        print memory[a].chr
    }
    elsif ((memory[b] -= memory[a]) <= 0) {
        ip = c
    }
}
```

#### Output:
```
$ sidef subleq.sf 15 17 -1 17 -1 -1 16 1 -1 16 3 -1 15 15 0 0 -1 72 101 108 108 111 44 32 119 111 114 108 100 33 10 0
Hello, world!
```
