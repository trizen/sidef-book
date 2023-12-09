[1]: https://rosettacode.org/wiki/Determine_if_a_string_is_collapsible

# [Determine if a string is collapsible][1]

```ruby
func squeeze(str) {
    str.gsub(/(.)\1+/, {|s1| s1 })
}
 
var strings = ["",
        '"If I were two-faced, would I be wearing this one?" --- Abraham Lincoln ',
        "..1111111111111111111111111111111111111111111111111111111111111117777888",
        "I never give 'em hell, I just tell the truth, and they think it's hell. ",
        "                                                   ---  Harry S Truman  ",
        "The better the 4-wheel drive, the further you'll be from help when ya get stuck!",
        "headmistressship",
        "aardvark",
        "😍😀🙌💃😍😍😍🙌"]
 
strings.each {|str|
    var ssq = squeeze(str)
    say "«««#{str}»»» (length: #{str.len})"
    say "«««#{ssq}»»» (length: #{ssq.len})\n"
}
```

#### Output:
```
«««»»» (length: 0)
«««»»» (length: 0)

«««"If I were two-faced, would I be wearing this one?" --- Abraham Lincoln »»» (length: 72)
«««"If I were two-faced, would I be wearing this one?" - Abraham Lincoln »»» (length: 70)

«««..1111111111111111111111111111111111111111111111111111111111111117777888»»» (length: 72)
«««.178»»» (length: 4)

«««I never give 'em hell, I just tell the truth, and they think it's hell. »»» (length: 72)
«««I never give 'em hel, I just tel the truth, and they think it's hel. »»» (length: 69)

«««                                                   ---  Harry S Truman  »»» (length: 72)
««« - Hary S Truman »»» (length: 17)

«««The better the 4-wheel drive, the further you'll be from help when ya get stuck!»»» (length: 80)
«««The beter the 4-whel drive, the further you'l be from help when ya get stuck!»»» (length: 77)

«««headmistressship»»» (length: 16)
«««headmistreship»»» (length: 14)

«««aardvark»»» (length: 8)
«««ardvark»»» (length: 7)

«««😍😀🙌💃😍😍😍🙌»»» (length: 8)
«««😍😀🙌💃😍🙌»»» (length: 6)
```
