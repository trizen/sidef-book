[1]: http://rosettacode.org/wiki/Truth_table

# [Truth table][1]

A simple solution which accepts arbitrary user-input:

```ruby
loop {
  var expr = Sys.readln("\nBoolean expression (e.g. 'a & b'): ").strip.lc
  break if expr.is_empty;
 
  var vars = expr.scan(/[[:alpha:]]+/)
  if (vars.is_empty) {
    say "no variables detected in your boolean expression"
    next
  }
 
  var prefix = [];
  var suffix = [];
 
  vars.each { |v|
    print "#{v}\t"
    prefix << "[false, true].each { |#{v}|"
    suffix << "}"
  }
  say "| #{expr}"
 
  var body = ("say (" + vars.map{|v| v+",'\t'," }.join + " '| ', #{expr})")
  eval(prefix + [body] + suffix -> join("\n"))
}
```

#### Output:
```
Boolean expression (e.g. 'a & b'): (a & b) | c
a       b       c       | (a & b) | c
false   false   false   | false
false   false   true    | true
false   true    false   | false
false   true    true    | true
true    false   false   | false
true    false   true    | true
true    true    false   | true
true    true    true    | true
```
