[1]: http://rosettacode.org/wiki/Huffman_coding

# [Huffman coding][1]

```ruby
func walk(n, s, h) {
    n.exists('a') && (
        h[n['a']] = s;
        say "#{n['a']}: #{s}";
        return;
    );
    walk(n['0'], s+'0', h);
    walk(n['1'], s+'1', h);
}
 
func make_tree(text) {
    var letters = Hash.new;
    text.each { |c| letters[c] := 0 ++ };
    var nodes = letters.keys.map { |l|
            Hash.new('a' => l, 'freq' => letters[l])
    };
 
    var n = Hash.new;
    while (nodes.sort!{|a,b| a['freq'] <=> b['freq'] }.len > 1) {
        n = Hash.new('0' => nodes.shift, '1' => nodes.shift);
        n['freq'] = (n['0']['freq'] + n['1']['freq']);
        nodes.append(n);
    }
 
    walk(n, '', n['tree'] = Hash.new);
    return n;
}
 
func encode(s, t) {
    t = t['tree'];
    s.split(1).join('' => {t[_]});
}
 
func decode (enc, tree) {
    var n = tree;
    var out = '';
 
    enc.each {|bit|
        (n = n[bit]).exists('a') && (
            out += n['a']; n = tree;
        );
    };
 
    return out;
}
 
var text = "this is an example for huffman encoding";
var tree = make_tree(text);
var enc = encode(text, tree);
 
say enc;
say decode(enc, tree);
```

#### Output:
```
n: 000
s: 0010
o: 0011
h: 0100
l: 01010
g: 01011
x: 01100
c: 01101
d: 01110
u: 01111
p: 10000
t: 10001
i: 1001
 : 101
f: 1100
a: 1101
e: 1110
r: 11110
m: 11111
1000101001001001010110010010101110100010111100110011011111110000010101110101110000111111010101000111111001100111111101000101111000001101001101110100100001011
this is an example for huffman encoding
```