[1]: http://rosettacode.org/wiki/Letter_frequency

# [Letter frequency][1]

```ruby
func letter_frequency(file) {
    file.open('<:utf8').slurp.split(1).grep{.match(/[[:alpha:]]/)}
        .group_by {|letter| letter.downcase}
        .map_val  {|_, val| val.len}
        .sort_by  {|_, val| -val}
}
 
var top = letter_frequency(File.new(__FILE__));
top.each{|pair| say "#{pair[0]}: #{pair[1]}"};
```

#### Output:
```
e: 22
l: 17
a: 16
t: 14
r: 14
p: 12
f: 8
i: 8
n: 7
c: 6
u: 6
o: 6
v: 6
y: 5
s: 5
h: 3
w: 2
q: 2
b: 2
m: 2
g: 2
d: 1
```