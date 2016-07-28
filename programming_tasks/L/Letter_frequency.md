[1]: http://rosettacode.org/wiki/Letter_frequency

# [Letter frequency][1]

```ruby
func letter_frequency(File file) {
    file.read.chars.grep{.match(/[[:alpha:]]/)} \
        .group_by {|letter| letter.downcase}    \
        .map_val  {|_, val| val.len}            \
        .sort_by  {|_, val| -val}
}
 
var top = letter_frequency(File(__FILE__))
top.each{|pair| say "#{pair[0]}: #{pair[1]}"}
```

#### Output:
```
e: 22
a: 18
l: 16
r: 15
t: 12
p: 9
f: 8
i: 8
c: 7
v: 6
y: 5
n: 5
o: 5
u: 4
h: 4
s: 4
b: 2
g: 2
m: 2
d: 2
q: 2
w: 1
```
