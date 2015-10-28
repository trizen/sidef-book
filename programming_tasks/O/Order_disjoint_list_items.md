[1]: http://rosettacode.org/wiki/Order_disjoint_list_items

# [Order disjoint list items][1]

```ruby
func dsort(m, n) {
    var h = Hash.new;
    n.each {|item| h{item} := 0 ++ };
    m.map  {|item| h{item} := 0 -- > 0 ? n.shift : item};
}
 
<<'EOT'.lines.each { |line|
        the cat sat on the mat  | mat cat
        the cat sat on the mat  | cat mat
        A B C A B C A B C       | C A C A
        A B C A B D A B E       | E A D A
        A B                     | B
        A B                     | B A
        A B B A                 | B A
EOT
        var (a, b) = line.split('|').map{.words}...;
        say "#{a} | #{b} -> #{dsort(a.copy, b.copy)}";
}
```

#### Output:
```
the cat sat on the mat | mat cat -> the mat sat on the cat
the cat sat on the mat | cat mat -> the cat sat on the mat
A B C A B C A B C | C A C A -> C B A C B A A B C
A B C A B D A B E | E A D A -> E B C A B D A B A
A B | B -> A B
A B | B A -> B A
A B B A | B A -> B A B A
```