[1]: https://rosettacode.org/wiki/Hofstadter_Figure-Figure_sequences

# [Hofstadter Figure-Figure sequences][1]

```ruby
var r = [nil, 1]
var s = [nil, 2]
 
func ffsr(n) {
  while(r.end < n) {
    r << s[r.end]+r[-1]
    s << [(s[-1]+1 .. r[-1]-1)..., r[-1]+1].grep{ s[-1] < _ }...
  }
  return n
}
 
func ffr(n) { r[ffsr(n)] }
func ffs(n) { s[ffsr(n)] }
 
printf("  i: R(i) S(i)\n")
printf("==============\n")
{ |i|
    printf("%3d:  %3d  %3d\n", i, ffr(i), ffs(i))
} << 1..10
printf("\nR(40)=%3d S(960)=%3d R(41)=%3d\n", ffr(40), ffs(960), ffr(41))
 
var seen = Hash()
 
{|i| seen{ffr(i)} := 0 ++ } << 1..40
{|i| seen{ffs(i)} := 0 ++ } << 1..960

if (seen.count {|k,v| (k.to_i >= 1) && (k.to_i <= 1000) && (v == 1) } == 1000) {
    say "All occured exactly once."
}
else {
    var missed = { !seen.has_key(_) }.grep(1..1000)
    var dupped = seen.grep { |_, v| v > 1 }.keys.sort
    say "These were missed: #{missed}"
    say "These were duplicated: #{dupped}"
}
```

#### Output:
```
  i: R(i) S(i)
==============
  1:    1    2
  2:    3    4
  3:    7    5
  4:   12    6
  5:   18    8
  6:   26    9
  7:   35   10
  8:   45   11
  9:   56   13
 10:   69   14

R(40)=982 S(960)=1000 R(41)=1030
All occured exactly once.
```
