[1]: https://rosettacode.org/wiki/Markov_chain_text_generator

# [Markov chain text generator][1]

```ruby
func build_dict (n, words) {
    var dict = Hash()
    for i in (0 .. words.len-n) {
        var prefix = words.slice(i, i+n-1)
        dict{prefix.join(' ')} := [] << words[i+n]
    }
    return dict
}
 
var file = File(ARGV[0] || "alice_oz.txt")
var n    =  Num(ARGV[1] || 2)
var max  =  Num(ARGV[2] || 100)
 
var words = file.open_r.words
var dict = build_dict(n, words)
 
var rotor = words.first(n)
var chain = [rotor...]
 
max.times {
    var new = dict{rotor.join(' ')}.rand
    chain.push(new)
    rotor.shift
    rotor.push(new)
}
 
say chain.join(' ')
```

#### Output:
```
Alice was a large caterpillar, that was linked into hers began to cry a little startled when she knows such a nice little histories about children who had always been used to; but neither were they very small. In fact, they seemed about as she had not been lying on the rocks below. But if you were down here with me! There are wild beasts in the house, quite forgetting that she stamped her foot as far as they moved. The hats of the East and West. Fortunately, the Witches of the fact. 'I keep them back, so they might rest until
```
