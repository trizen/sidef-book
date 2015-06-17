[1]: http://rosettacode.org/wiki/Letter_frequency

# [Letter frequency][1]

```ruby
func letter_frequency(file) {
    file.open('<:utf8').slurp.split(1).grep{.matches(/[[:alpha:]]/)}
        .group_by {|letter| letter.downcase}
        .map_val  {|_, val| val.len}
        .sort_by  {|_, val| -val}
}
 
var top = letter_frequency(File.new(__FILE__));
top.each{|key, val| say "#{key}: #{val}"};
```

#### Output:
```
e: 25
l: 19
a: 15
t: 14
r: 11
p: 9
v: 8
f: 8
n: 7
y: 7
o: 6
c: 6
u: 6
s: 6
i: 5
h: 3
w: 2
m: 2
b: 2
q: 2
g: 2
k: 2
d: 1
```