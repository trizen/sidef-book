[1]: https://rosettacode.org/wiki/Universal_Turing_machine

# [Universal Turing machine][1]

```ruby
func run_utm(state="", blank="", rules=[], tape=[blank], halt="", pos=0) {
 
    if (pos < 0) {
        pos += tape.len;
    }
 
    if (pos !~ tape.range) {
        die "Bad initial position";
    }
 
    loop {
        print "#{state}\t";
        tape.range.each { |i|
            var v = tape[i];
            print (i == pos ? "[#{v}]" : " #{v} ");
        };
        print "\n";
 
        if (state == halt) {
            break;
        }
 
        for s0, v0, v1, dir, s1 in rules {
            if ((s0 != state) || (tape[pos] != v0)) {
                next;
            }
 
            tape[pos] = v1;
 
            given(dir) {
                when ('left') {
                     if (pos == 0) { tape.unshift(blank) }
                     else          { --pos };
                }
                when ('right') {
                    if (++pos >= tape.len) {
                        tape.append(blank)
                    }
                }
            }
 
            state = s1;
            goto :NEXT;
        }
 
        die 'No matching rules';
        @:NEXT;
    }
}
 
print "incr machine\n";
run_utm(
    halt:  'qf',
    state: 'q0',
    tape:  %w(1 1 1),
    blank: 'B',
    rules: [
        %w(q0 1 1 right q0),
        %w(q0 B 1 stay  qf),
    ]);
 
say "\nbusy beaver";
run_utm(
    halt:  'halt',
    state: 'a',
    blank: '0',
    rules: [
        %w(a 0 1 right b),
        %w(a 1 1 left  c),
        %w(b 0 1 left  a),
        %w(b 1 1 right b),
        %w(c 0 1 left  b),
        %w(c 1 1 stay  halt),
    ]);
 
say "\nsorting test";
run_utm(
    halt:  'STOP',
    state: 'A',
    blank: '0',
    tape:  %w(2 2 2 1 2 2 1 2 1 2 1 2 1 2),
    rules: [
        %w(A 1 1 right A),
        %w(A 2 3 right B),
        %w(A 0 0 left  E),
        %w(B 1 1 right B),
        %w(B 2 2 right B),
        %w(B 0 0 left  C),
        %w(C 1 2 left  D),
        %w(C 2 2 left  C),
        %w(C 3 2 left  E),
        %w(D 1 1 left  D),
        %w(D 2 2 left  D),
        %w(D 3 1 right A),
        %w(E 1 1 left  E),
        %w(E 0 0 right STOP),
    ]);
```
