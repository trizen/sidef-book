[1]: http://rosettacode.org/wiki/Executable_library

# [Executable library][1]

Library saved as *Hailstone.sm*

```ruby
func hailstone(n) {
    gather {
        while (n > 1) {
            take(n)
            n = (n.is_even ? n/2 : (3*n + 1))
        }
        take(1)
    }
}
 
if (__FILE__ == __MAIN__) {             # true when not imported
    var seq = hailstone(27)
    say "hailstone(27) - #{seq.len} elements: #{seq.ft(0, 3)} [...] #{seq.ft(-4)}"
 
    var n = 0
    var max = 0
    100_000.times { |i|
        var seq = hailstone(i)
        if (seq.len > max) {
            max = seq.len
            n = i
        }
    }
 
    say "Longest sequence is for #{n}: #{max}"
}
```


It can be run with:

```text
$ sidef Hailstone.sm
```


It can then be used with a program such as:

```ruby
include Hailstone
 
var score = Hash()
100_000.times { |i| score{ Hailstone::hailstone(i).len } := 0 ++ }
 
var k = score.keys.max_by {|k| score{k} }
say "Most common length is #{k}, occurring #{score{k}} times"
```


Called with a command line as:

```text
$ sidef test_hailstone.sf
```


The library is searched in the directories specified in the *SIDEF\_INC* environment variable, which defaults to the current directory.
