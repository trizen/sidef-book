[1]: http://rosettacode.org/wiki/Text_processing/Max_licenses_in_use

# [Text processing/Max licenses in use][1]

```ruby
var out = 0;
var max_out = -1;
var max_times = [];
 
ARGF.each { |line|
    out += (line ~~ /OUT/ ? 1 : -1);
    out > max_out && (
        max_out = out;
        max_times = [];
    );
    out == max_out && (
        max_times << line.split(' ')[3];
    );
}
 
say "Maximum simultaneous license use is #{max_out} at the following times:";
max_times.each {|t| "  #{t}".say };
```

#### Output:
```
$ sidef max_licenses.sf < mlijobs.txt
Maximum simultaneous license use is 99 at the following times:
  2008/10/03_08:39:34
  2008/10/03_08:40:40
```