[1]: https://rosettacode.org/wiki/Checksumcolor

# [Checksumcolor][1]

```ruby
var ansi = frequire("Term::ANSIColor")
 
func colorhash(hash) {
    hash.split(2).map{|s| ansi.colored(s, "ansi" + s.hex) }.join
}
 
ARGF.each {|line|
    if (STDOUT.is_on_tty && (line =~ /^([[:xdigit:]]+)(.*)/)) {|m|
        say (colorhash(m[0]), m[1])
    }
    else {
        say line
    }
}
```

<div style="background-color:black; color:white; width:600px; font-size:100%; font-family: Monaco, monospace;">

<font color="#FF5252">% </font>md5sum \*.sf | sf checksumcolor.sf


<font color="#A8A8A8">f8</font><font color="#D78700">ac</font><font color="#42A5F5">04</font><font color="#D7FFAF">c1</font><font color="#AF5FAF">85</font><font color="#AF0000">7c</font><font color="#000000">10</font><font color="#AFAFAF">91</font><font color="#5F87FF">45</font><font color="#FFD7FF">e1</font><font color="#D7FF5F">bf</font><font color="#F5F5F5">0f</font><font color="#FFFF00">e2</font><font color="#5FFFAF">55</font><font color="#5FD7D7">50</font><font color="#FF8787">d2</font> checksumcolor (copy).sf


<font color="#A8A8A8">f8</font><font color="#D78700">ac</font><font color="#42A5F5">04</font><font color="#D7FFAF">c1</font><font color="#AF5FAF">85</font><font color="#AF0000">7c</font><font color="#000000">10</font><font color="#AFAFAF">91</font><font color="#5F87FF">45</font><font color="#FFD7FF">e1</font><font color="#D7FF5F">bf</font><font color="#F5F5F5">0f</font><font color="#FFFF00">e2</font><font color="#5FFFAF">55</font><font color="#5FD7D7">50</font><font color="#FF8787">d2</font> checksumcolor.sf


<font color="#D787AF">af</font><font color="#708284">08</font><font color="#8787FF">69</font><font color="#5F875F">41</font><font color="#D7AFD7">b6</font><font color="#FFD700">dc</font><font color="#8787AF">67</font><font color="#252525">00</font><font color="#008700">1c</font><font color="#FFAF87">d8</font><font color="#00FFAF">31</font><font color="#D7D7AF">bb</font><font color="#0087AF">1f</font><font color="#00AF00">22</font><font color="#D7FFFF">c3</font><font color="#3A3A3A">ed</font> farey.sf


<font color="#D7AFAF">b5</font><font color="#AF5FAF">85</font><font color="#D7FFD7">c2</font><font color="#5FD7FF">51</font><font color="#5FAF00">46</font><font color="#121212">e9</font><font color="#5FD75F">4d</font><font color="#767676">f3</font><font color="#87D700">70</font><font color="#303030">ec</font><font color="#5FAF87">48</font><font color="#5FAF00">46</font><font color="#8787FF">69</font><font color="#00005F">11</font><font color="#FFAFAF">d9</font><font color="#D78787">ae</font> pell.sf

</div>
