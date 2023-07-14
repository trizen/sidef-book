[1]: https://rosettacode.org/wiki/Change_e_letters_to_i_in_words

# [Change e letters to i in words][1]

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

var words = file.read.words
var dict  = Hash().set_keys(words...)
var count = 0

words.each {|word|

    word.len > 5 || next
    word.contains('e') || next

    var changed = word.gsub('e', 'i')

    if (dict.contains(changed)) {
        printf("%2d: %20s <-> %s\n", ++count, word, changed)
    }
}
```

#### Output:
```
 1:             analyses <-> analysis
 2:             atlantes <-> atlantis
 3:               bellow <-> billow
 4:               breton <-> briton
 5:               clench <-> clinch
 6:              convect <-> convict
 7:               crises <-> crisis
 8:            diagnoses <-> diagnosis
 9:               enfant <-> infant
10:              enquiry <-> inquiry
11:              frances <-> francis
12:              galatea <-> galatia
13:               harden <-> hardin
14:              heckman <-> hickman
15:             inequity <-> iniquity
16:              inflect <-> inflict
17:             jacobean <-> jacobian
18:               marten <-> martin
19:               module <-> moduli
20:              pegging <-> pigging
21:            psychoses <-> psychosis
22:               rabbet <-> rabbit
23:             sterling <-> stirling
24:             synopses <-> synopsis
25:               vector <-> victor
26:               welles <-> willis
```
