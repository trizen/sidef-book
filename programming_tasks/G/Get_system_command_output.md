[1]: http://rosettacode.org/wiki/Get_system_command_output

# [Get system command output][1]

Using backticks:

```ruby
var output = `ls`;           # `output` is a string
var lines  = `ls`.lines;     # `lines` is an array
```


Using pipes:

```ruby
var pipe   = %p(ls);          # same as: Pipe.new('ls');
var pipe_h = pipe.open_r;     # open the pipe for reading
var lines  = [];              # will store the lines of the output
pipe_h.each { |line| lines.append(line.chomp) };
```