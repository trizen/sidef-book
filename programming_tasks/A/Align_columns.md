[1]: https://rosettacode.org/wiki/Align_columns

# [Align columns][1]

```ruby
class Format(text, width) {
    method align(j) {
        text.map { |row|
            row.range.map { |i|
                '%-*s ' % (width[i],
                  '%*s' % (row[i].len + (width[i]-row[i].len * j/2), row[i]));
            }.join("");
        }.join("\n") + "\n";
    }
}
 
func Formatter(text) {
    var textArr = [];
    var widthArr = [];
 
    text.each_line {
        var words = .split('$');
        textArr.append(words);
 
        words.each_kv { |i, word|
            if (i == widthArr.len) {
                widthArr.append(word.len);
            }
            elsif (word.len > widthArr[i]) {
                widthArr[i] = word.len;
            }
        }
    }
 
    return Format(textArr, widthArr);
}
 
enum |left, middle, right|;
const text = <<'EOT';
Given$a$text$file$of$many$lines,$where$fields$within$a$line$
are$delineated$by$a$single$'dollar'$character,$write$a$program
that$aligns$each$column$of$fields$by$ensuring$that$words$in$each$
column$are$separated$by$at$least$one$space.
Further,$allow$for$each$word$in$a$column$to$be$either$left$
justified,$right$justified,$or$center$justified$within$its$column.
EOT
 
var f = Formatter(text);
 
say f.align(left);
say f.align(middle);
say f.align(right);
```
