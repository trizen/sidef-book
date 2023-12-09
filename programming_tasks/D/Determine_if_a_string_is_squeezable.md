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

#### Output:
```
    original: «««»»» (length: 0)

    original: «««"If I were two-faced, would I be wearing this one?" --- Abraham Lincoln »»» (length: 72)
'-'-squeezed: «««"If I were two-faced, would I be wearing this one?" - Abraham Lincoln »»» (length: 70)

    original: «««..1111111111111111111111111111111111111111111111111111111111111117777888»»» (length: 72)
'7'-squeezed: «««..1111111111111111111111111111111111111111111111111111111111111117888»»» (length: 69)

    original: «««I never give 'em hell, I just tell the truth, and they think it's hell. »»» (length: 72)
'.'-squeezed: «««I never give 'em hell, I just tell the truth, and they think it's hell. »»» (length: 72)

    original: «««                                                   ---  Harry S Truman  »»» (length: 72)
' '-squeezed: ««« --- Harry S Truman »»» (length: 20)
'-'-squeezed: «««                                                   -  Harry S Truman  »»» (length: 70)
'r'-squeezed: «««                                                   ---  Hary S Truman  »»» (length: 71)

    original: «««😍😀🙌💃😍😍😍🙌»»» (length: 8)
'😍'-squeezed: «««😍😀🙌💃😍🙌»»» (length: 6)
```
