[1]: https://rosettacode.org/wiki/Decision_tables

# [Decision tables][1]

```ruby
func decide (q, s) {
 
    var bits = q.map { |p|
        read("#{p.value}? ", String) ~~ /^y/i ? 1 : 0
    }
 
    var n = with (0) { |t|
        bits.each { |b|
            t <<= 1
            t |= b
        }
        1 << t
    }
 
    s.grep { .key & n }.map{ .value }.each { |ans|
        say "   #{ans}"
    }
}
 
loop {
    decide(
      [
        Pair("Y Y Y Y N N N N", "Printer does not print"),
        Pair("Y Y N N Y Y N N", "A red light is flashing"),
        Pair("Y N Y N Y N Y N", "Printer is unrecognised"),
      ],
      [
        Pair(0b0_0_1_0_0_0_0_0, "Check the power cable"),
        Pair(0b1_0_1_0_0_0_0_0, "Check the printer-computer cable"),
        Pair(0b1_0_1_0_1_0_1_0, "Ensure printer software is installed"),
        Pair(0b1_1_0_0_1_1_0_0, "Check/replace ink"),
        Pair(0b0_1_0_1_0_0_0_0, "Check for paper jam"),
      ]
    )
    say ''
}
```

#### Output:
```
Printer does not print? y
A red light is flashing? n
Printer is unrecognised? n
   Check for paper jam

Printer does not print? n
A red light is flashing? n
Printer is unrecognised? y
   Ensure printer software is installed

Printer does not print? y
A red light is flashing? y
Printer is unrecognised? n
   Check/replace ink
   Check for paper jam

Printer does not print? n
A red light is flashing? y
Printer is unrecognised? y
   Ensure printer software is installed
   Check/replace ink

Printer does not print? ^C
```