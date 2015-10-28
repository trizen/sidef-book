[1]: http://rosettacode.org/wiki/Word_wrap

# [Word wrap][1]

Greedy:

```ruby
class String {
    method wrap(width) {
        var txt = self.gsub(/\s+/, " ");
        var len = txt.len;
        var para = [];
        var i = 0;
        while (i < len) {
            var j = (i + width);
            while ((j < len) && (txt.char_at(j) != ' ')) { --j };
            para.append(txt.substr(i, j-i));
            i = j+1;
        };
        return para.join("\n");
    }
}
 
var text = 'aaa bb cc ddddd';
say text.wrap(6);
```

#### Output:
```
aaa bb
cc
ddddd
```


Smart:

```ruby
class SmartWordWrap(WIDTH=80) {
    method prepare_words(array) {
 
        var root = [];
        var len  = 0;
 
        for (var i = 0 ; i <= array.end ; i++) {
            var word_len = array[i].len;
            len += word_len;
 
            len > WIDTH && (
                word_len > WIDTH && (
                    len -= word_len;
                    array.splice(i, 1, array[i].split(WIDTH)...);
                    --i; next;
                );
                break;
            );
 
            root.append(Hash.new(array.ft(0, i).join(" ")
                => self.prepare_words(array.ft(i + 1, array.end))));
            ++len >= WIDTH && break;
        }
 
        root ? root : Null;
    }
 
    method combine(root, hash) {
 
        var row = [];
        hash.each { |key, value|
            root.append(key);
 
            if (value.is_an(Array)) {
                value.each { |item|
                    row.append(self.combine(root, item)...);
                }
            }
            else {
                row = [[root...]];
            };
            root.pop;
        };
 
        row;
    }
 
    method find_best(arrays) {
 
        var best = Hash.new(
            score => Math.inf,
            value => [],
        );
 
        arrays.each { |array_ref|
            var score = 0;
 
            array_ref.each { |string|
                score += Math.pow(WIDTH - string.len, 2);
            }
 
            score < best{:score} && (
                best{:score} = score;
                best{:value} = array_ref;
            );
        }
 
        best{:value};
    }
 
    method wrap(text) {
 
        # Split the text into words
        text.is_a(String) && text.words!;
 
        var lines = [];
        self.prepare_words(text).each { |path|
            lines.append(self.combine([], path)...);
        };
 
        self.find_best(lines).join("\n");
    }
}
 
var sww = SmartWordWrap(WIDTH: 6);
 
var words = %w(aaa bb cc ddddd);
var wrapped = sww.wrap(words);
 
say wrapped;
```

#### Output:
```
aaa
bb cc
ddddd
```