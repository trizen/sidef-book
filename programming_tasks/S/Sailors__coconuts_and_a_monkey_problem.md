[1]: http://rosettacode.org/wiki/Sailors,_coconuts_and_a_monkey_problem

# [Sailors, coconuts and a monkey problem][1]

```ruby
func coconuts(sailor) {
    range(sailor, Math.inf, sailor).each { |nuts|
        sailor.times {
            nuts % (sailor-1) != 0 && goto :NEXT;
            nuts += (nuts / (sailor-1) + 1);
        }
        return nuts;
        @:NEXT;
    }
}
 
range(2, 9).each { |sailor|
    say "#{sailor}: #{coconuts(sailor)}";
}
```

#### Output:
```
2: 11
3: 25
4: 765
5: 3121
6: 233275
7: 823537
8: 117440505
9: 387420481
```