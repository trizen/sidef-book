[1]: https://rosettacode.org/wiki/Text_between

# [Text between][1]

Uses /^/ and /$/ as start and end delimiters. Additionally, the start and end delimiters can be regular expressions.

```ruby
func text_between (text, beg, end) {
 
    beg.escape! if beg.kind_of(String)
    end.escape! if end.kind_of(String)
 
    Regex("#{beg}(.*?)(?:#{end}|\\z)", 's').match(text)[0] \\ ""
}
 
var tests = [
    Hash(
        text  => "Hello Rosetta Code world",
        start => "Hello ",
        end   => " world",
        out   => "Rosetta Code",
    ),
    Hash(
        text  => "Hello Rosetta Code world",
        start => /^/,
        end   => " world",
        out   => "Hello Rosetta Code",
    ),
    Hash(
        text  => "Hello Rosetta Code world",
        start => "Hello ",
        end   => /$/,
        out   => "Rosetta Code world",
    ),
    Hash(
        text  => "</div><div style=\"chinese\">你好嗎</div>",
        start => "<div style=\"chinese\">",
        end   => "</div>",
        out   => "你好嗎",
    ),
    Hash(
        text  => "<text>Hello <span>Rosetta Code</span> world</text><table style=\"myTable\">",
        start => "<text>",
        end   => "<table>",
        out   => "Hello <span>Rosetta Code</span> world</text><table style=\"myTable\">",
    ),
    Hash(
        text  => "<table style=\"myTable\"><tr><td>hello world</td></tr></table>",
        start => "<table>",
        end   => "</table>",
        out   => "",
    ),
    Hash(
        text  => "The quick brown fox jumps over the lazy other fox",
        start => "quick ",
        end   => " fox",
        out   => "brown",
    ),
    Hash(
        text  => "One fish two fish red fish blue fish",
        start => "fish ",
        end   => " red",
        out   => "two fish",
    ),
    Hash(
        text  => "FooBarBazFooBuxQuux",
        start => "Foo",
        end   => "Foo",
        out   => "BarBaz",
    ),
]
 
tests.each { |t|
    var r = text_between(t{:text}, t{:start}, t{:end})
    assert_eq(t{:out}, r)
    say "text_between(#{t{:text}.dump}, #{t{:start}.dump}, #{t{:end}.dump}) = #{r.dump}"
}
```

#### Output:
```
text_between("Hello Rosetta Code world", "Hello ", " world") = "Rosetta Code"
text_between("Hello Rosetta Code world", /^/, " world") = "Hello Rosetta Code"
text_between("Hello Rosetta Code world", "Hello ", /$/) = "Rosetta Code world"
text_between("</div><div style=\"chinese\">\x{4F60}\x{597D}\x{55CE}</div>", "<div style=\"chinese\">", "</div>") = "\x{4F60}\x{597D}\x{55CE}"
text_between("<text>Hello <span>Rosetta Code</span> world</text><table style=\"myTable\">", "<text>", "<table>") = "Hello <span>Rosetta Code</span> world</text><table style=\"myTable\">"
text_between("<table style=\"myTable\"><tr><td>hello world</td></tr></table>", "<table>", "</table>") = ""
text_between("The quick brown fox jumps over the lazy other fox", "quick ", " fox") = "brown"
text_between("One fish two fish red fish blue fish", "fish ", " red") = "two fish"
text_between("FooBarBazFooBuxQuux", "Foo", "Foo") = "BarBaz"
```