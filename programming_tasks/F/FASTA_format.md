[1]: https://rosettacode.org/wiki/FASTA_format

# [FASTA format][1]

```ruby
func fasta_format(strings) {
    var out = []
    var text = ''
    for line in (strings.lines) {
        if (line.begins_with('>')) {
            text.len && (out << text)
            text = line.substr(1)+': '
        }
        else {
            text += line
        }
    }
    text.len && (out << text)
    return out
}
 
fasta_format(DATA.slurp).each { .say }
 
__DATA__
>Rosetta_Example_1
THERECANBENOSPACE
>Rosetta_Example_2
THERECANBESEVERAL
LINESBUTTHEYALLMUST
BECONCATENATED
```

#### Output:
```
Rosetta_Example_1: THERECANBENOSPACE
Rosetta_Example_2: THERECANBESEVERALLINESBUTTHEYALLMUSTBECONCATENATED
```