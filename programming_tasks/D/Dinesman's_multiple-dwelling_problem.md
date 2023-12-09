[1]: https://rosettacode.org/wiki/Dinesman's_multiple-dwelling_problem

# [Dinesman's multiple-dwelling problem][1]

### By parsing the problem

```ruby
func dinesman(problem) {
  var lines = problem.split('.')
  var names = lines.first.scan(/\b[A-Z]\w*/)
  var re_names = Regex(names.join('|'))
 
  # Later on, search for these keywords (the word "not" is handled separately).
  var words = %w(first second third fourth fifth sixth seventh eighth ninth tenth
                 bottom top higher lower adjacent)
  var re_keywords = Regex(words.join('|'))
 
  # Build an array of lambda's
  var predicates = lines.first(-1).last(-1).map{ |line|
    var keywords = line.scan(re_keywords)
    var (name1, name2) = line.scan(re_names)...
 
    keywords.map{ |keyword|
      var l = do {
        given(keyword) {
            when ("bottom")   { ->(c) { c.first == name1 } }
            when ("top")      { ->(c) { c.last == name1 } }
            when ("higher")   { ->(c) { c.index(name1) > c.index(name2) } }
            when ("lower")    { ->(c) { c.index(name1) < c.index(name2) } }
            when ("adjacent") { ->(c) { c.index(name1) - c.index(name2) -> abs == 1 } }
            default           { ->(c) { c[words.index(keyword)] == name1 } }
        }
      }
      line ~~ /\bnot\b/ ? func(c) { l(c) -> not } : l;  # handle "not"
    }
  }.flat
 
  names.permutations { |*candidate|
    predicates.all { |predicate| predicate(candidate) } && return candidate
  }
}
```


Function invocation:

```ruby
var demo1 = "Abe Ben Charlie David. Abe not second top. not adjacent Ben Charlie.
David Abe adjacent. David adjacent Ben. Last line."
 
var demo2 = "A B C D. A not adjacent D. not B adjacent higher C. C lower D. Last line"
 
var problem1 = "Baker, Cooper, Fletcher, Miller, and Smith live on different floors of an apartment house that
contains only five floors. Baker does not live on the top floor. Cooper does not live on the bottom floor.
Fletcher does not live on either the top or the bottom floor. Miller lives on a higher floor than does Cooper.
Smith does not live on a floor adjacent to Fletcher's. Fletcher does not live on a floor adjacent to Cooper's.
Where does everyone live?"
 
var problem2 = "Baker, Cooper, Fletcher, Miller, Guinan, and Smith
live on different floors of an apartment house that contains
only seven floors. Guinan does not live on either the top or the third or the fourth floor.
Baker does not live on the top floor. Cooper
does not live on the bottom floor. Fletcher does not live on
either the top or the bottom floor. Miller lives on a higher
floor than does Cooper. Smith does not live on a floor
adjacent to Fletcher's. Fletcher does not live on a floor
adjacent to Cooper's. Where does everyone live?"
 
[demo1, demo2, problem1, problem2].each{|problem| say dinesman(problem).join("\n"); say '' }
```

#### Output:
```
Ben
David
Abe
Charlie

B
A
C
D

Smith
Cooper
Baker
Fletcher
Miller

Baker
Cooper
Miller
Fletcher
Guinan
Smith
```


### Simple solution

```ruby
var names = %w(Baker Cooper Fletcher Miller Smith)
 
var predicates = [
    ->(c){ :Baker != c.last },
    ->(c){ :Cooper != c.first },
    ->(c){ (:Fletcher != c.first) && (:Fletcher != c.last) },
    ->(c){ c.index(:Miller) > c.index(:Cooper) },
    ->(c){ (c.index(:Smith) - c.index(:Fletcher)).abs != 1 },
    ->(c){ (c.index(:Cooper) - c.index(:Fletcher)).abs != 1 },
]
 
names.permutations { |*candidate|
    if (predicates.all {|predicate| predicate(candidate) }) {
        say candidate.join("\n")
        break
    }
}
```

#### Output:
```
Smith
Cooper
Baker
Fletcher
Miller
```
