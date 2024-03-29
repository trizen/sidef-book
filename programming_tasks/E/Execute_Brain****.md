[1]: https://rosettacode.org/wiki/Execute_Brain****

# [Execute Brain****][1]

```ruby
define tape_length = 50_000;
define eof_val = -1;
define unbalanced_exit_code = 1;
 
var cmd = 0;
var cell = 0;
var code = [];
var loops = [];
var tape = tape_length.of(0);
 
func get_input {
    static input_buffer = [];
    input_buffer.len || (input_buffer = ((STDIN.readline \\ return eof_val).chomp.chars.map{.ord}));
    input_buffer.shift \\ eof_val;
}
 
func jump {
    var depth = 0;
    while (depth >= 0) {
        ++cmd < code.len || Sys.exit(unbalanced_exit_code);
        if (code[cmd] == '[') {
            ++depth;
        }
        elsif (code[cmd] == ']') {
            --depth;
        }
    }
}
 
var commands = Hash.new(
    '>' => { ++cell },
    '<' => { --cell },
    '+' => { ++tape[cell] },
    '-' => { --tape[cell] },
    '.' => { tape[cell].chr.print },
    ',' => { tape[cell] = get_input() },
    '[' => { tape[cell] ? loops.append(cmd) : jump() },
    ']' => { cmd = (loops.pop - 1) },
);
 
STDOUT.autoflush(1);
code = ARGF.slurp.chars.grep {|c| commands.exists(c)};
var code_len = code.len;
 
while (cmd < code_len) {
    commands{code[cmd]}.run;
    cmd++;
}
```