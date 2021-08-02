[1]: https://rosettacode.org/wiki/Changeable_words

# [Changeable words][1]

```ruby
var file = File("unixdict.txt")
 
if (!file.exists) {
    require('LWP::Simple')
    say ":: Retrieving #{file} from internet..."
    %S<LWP::Simple>.mirror(
        'https://web.archive.org/web/20180611003215if_/' +
        'http://www.puzzlers.org:80/pub/wordlists/unixdict.txt',
    'unixdict.txt')
}
 
var words  = file.read.words
var bucket = Hash()
var count = 0
 
words.each {|word|
 
    var len = word.len
 
    len > 11 || next
    bucket{len} := []
 
    bucket{len}.each{|prev|
        if (prev ^ word -> count("\0") == len-1) {
            printf("%2d: %20s <-> %s\n", ++count, prev, word)
        }
    }
    bucket{len} << word
}
```

#### Output:
```
 1:         aristotelean <-> aristotelian
 2:       claustrophobia <-> claustrophobic
 3:         committeeman <-> committeemen
 4:       committeewoman <-> committeewomen
 5:        complementary <-> complimentary
 6:         confirmation <-> conformation
 7:        congresswoman <-> congresswomen
 8:         councilwoman <-> councilwomen
 9:         craftsperson <-> draftsperson
10:         eavesdropped <-> eavesdropper
11:         frontiersman <-> frontiersmen
12:       handicraftsman <-> handicraftsmen
13:         incommutable <-> incomputable
14:         installation <-> instillation
15:         kaleidescope <-> kaleidoscope
16:         neuroanatomy <-> neuroanotomy
17:         newspaperman <-> newspapermen
18:         nonagenarian <-> nonogenarian
19:         onomatopoeia <-> onomatopoeic
20:         philanthrope <-> philanthropy
21:         prescription <-> proscription
22:        schizophrenia <-> schizophrenic
23:        shakespearean <-> shakespearian
24:         spectroscope <-> spectroscopy
25:        underclassman <-> underclassmen
26:        upperclassman <-> upperclassmen
```
