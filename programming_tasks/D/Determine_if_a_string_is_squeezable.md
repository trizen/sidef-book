[1]: https://rosettacode.org/wiki/Determine_if_a_string_is_squeezable

# [Determine if a string is squeezable][1]

```ruby
func squeeze(str, c) {
    str.gsub(Regex("(" + c.escape + ")" + '\1+'), {|s1| s1 })
}
 
var strings = ["",
        '"If I were two-faced, would I be wearing this one?" --- Abraham Lincoln ',
        "..1111111111111111111111111111111111111111111111111111111111111117777888",
        "I never give 'em hell, I just tell the truth, and they think it's hell. ",
        "                                                   ---  Harry S Truman  ",
        "😍😀🙌💃😍😍😍🙌"]
 
var squeeze_these = ["", "-", "7", ".", " -r", "😍"]
 
[strings, squeeze_these].zip {|str,st|
    say "    original: «««#{str}»»» (length: #{str.len})"
    st.each {|c|
        var ssq = squeeze(str, c)
        say "'#{c}'-squeezed: «««#{ssq}»»» (length: #{ssq.len})"
    }
    say ''
}
```
