[1]: https://rosettacode.org/wiki/Execute_HQ9+

# [Execute HQ9+][1]

```ruby
class HQ9Interpreter {
    has pointer;
    has accumulator;
 
    func bob (beer) {
        func what  { "#{beer ? beer : 'No more'} bottle#{beer-1 ? 's' : ''} of beer" }
        func where { 'on the wall' }
        func drink { beer--; "Take one down, pass it around," }
 
        while (beer.is_pos) {
            [[what(), where()], [what()],
            [drink()], [what(), where()], []].each{.join(' ').say}
        }
    }
 
    method run (code) {
        var chars = code.chars;
        accumulator = 0;
        pointer = 0;
        while (pointer < chars.len) {
            given (chars[pointer].lc) {
                when ('h') { say 'Hello world!' }
                when ('q') { say code }
                when ('9') { bob(99) }
                when ('+') { accumulator++ }
                default    { warn %Q(Syntax error: Unknown command "#{chars[pointer]}") }
            }
            pointer++;
        }
    }
}
```


Usage:

```ruby
var hq9 = HQ9Interpreter();
hq9.run("hHq+++Qq");
```

#### Output:
```
Hello world!
Hello world!
hHq+++Qq
hHq+++Qq
hHq+++Qq
```


Or start a REPL (Read Execute Print Loop) and interact at the command line:

```ruby
var hq9 = HQ9Interpreter();
loop {
    var in = read('HQ9+>', String) \\ break;
    hq9.run(in)
}
```