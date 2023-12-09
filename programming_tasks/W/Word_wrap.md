[1]: https://rosettacode.org/wiki/Word_wrap

# [Word wrap][1]

### Greedy word wrap

```ruby
class String {
    method wrap(width) {
        var txt = self.gsub(/\s+/, " ")
        var len = txt.len
        var para = []
        var i = 0
        while (i < len) {
            var j = (i + width)
            while ((j < len) && (txt.char_at(j) != ' ')) { --j }
            para.append(txt.substr(i, j-i))
            i = j+1
        }
        return para.join("\n")
    }
}
 
var text = 'aaa bb cc ddddd'
say text.wrap(6)
```

#### Output:
```
aaa bb
cc
ddddd
```


### Smart word wrap

```ruby
class SmartWordWrap {

    has width = 80

    method prepare_words(array, depth=0, callback) {

        var root = []
        var len = 0
        var i = -1

        var limit = array.end
        while (++i <= limit) {
            len += (var word_len = array[i].len)

            if (len > width) {
                if (word_len > width) {
                    len -= word_len
                    array.splice(i, 1, array[i].split(width)...)
                    limit = array.end
                    --i; next
                }
                break
            }

            root << [
                array.first(i+1).join(' '),
                self.prepare_words(array.slice(i+1), depth+1, callback)
            ]

            if (depth.is_zero) {
                callback(root[0])
                root = []
            }

            break if (++len >= width)
        }

        root
    }

    method combine(root, path, callback) {
        var key = path.shift
        path.each { |value|
            root << key
            if (value.is_empty) {
                callback(root)
            }
            else {
                value.each { |item|
                    self.combine(root, item, callback)
                }
            }
            root.pop
        }
    }

    method wrap(text, width) {

        self.width = width
        var words = (text.kind_of(Array) ? text : text.words)

        var best = Hash(
            score => Inf,
            value => [],
        )

        self.prepare_words(words, callback: { |path|
            self.combine([], path, { |combination|
                var score = 0
                combination.first(-1).each { |line|
                    score += (width - line.len -> sqr)
                }

                if (score < best{:score}) {
                    best{:score} = score
                    best{:value} = []+combination
                }
            })
        })

        best{:value}.join("\n")
    }
}
 
var sww = SmartWordWrap()
 
var words = %w(aaa bb cc ddddd)
var wrapped = sww.wrap(words, 6)
 
say wrapped
```

#### Output:
```
aaa
bb cc
ddddd
```
