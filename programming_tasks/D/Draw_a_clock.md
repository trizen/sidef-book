[1]: https://rosettacode.org/wiki/Draw_a_clock

# [Draw a clock][1]

```ruby
STDOUT.autoflush(true)

var (rows, cols) = `stty size`.nums...

var x = (rows/2 - 1  -> int)
var y = (cols/2 - 16 -> int)

var chars = [
                 "┌─┐  ╷╶─┐╶─┐╷ ╷┌─╴┌─╴╶─┐┌─┐┌─┐   ",
                 "│ │  │┌─┘╶─┤└─┤└─┐├─┐  │├─┤└─┤ : ",
                 "└─┘  ╵└─╴╶─┘  ╵╶─┘└─┘  ╵└─┘╶─┘   "
             ].map {|s| s.split(3) }

func position(i,j) {
    "\e[%d;%dH" % (i, j)
}

func indices {
    var t = Time.local
    "%02d:%02d:%02d" % (t.hour, t.min, t.sec) -> split(1).map{|c| c.ord - '0'.ord }
}

loop {
    print "\e[H\e[J"
    for i in ^chars {
      print position(x + i, y)
      print [chars[i][indices()]].join(' ')
    }
    print position(1, 1)
    Sys.sleep(0.1)
}
```

#### Output:
```
   ╷ ┌─╴     ╷ ╷ ┌─┐     ╶─┐ ┌─╴
   │ └─┐  :  └─┤ └─┤  :  ╶─┤ └─┐
   ╵ ╶─┘       ╵ ╶─┘     ╶─┘ ╶─┘
```
