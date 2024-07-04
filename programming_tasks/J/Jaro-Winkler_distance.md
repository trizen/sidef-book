[1]: https://rosettacode.org/wiki/Jaro-Winkler_distance

# [Jaro-Winkler distance][1]

Reusing the *jaro()* function from the [Jaro similarity](https://rosettacode.org/wiki/Jaro_similarity#Sidef) task.

```ruby
func jaro_winkler_distance(s,t) {

    var jaro_similarity = jaro(s, t)

    var prefix = 0
    for i in (0 .. min(3, s.len, t.len)) {
        s.char(i) == t.char(i) ? ++prefix : break
    }

    1 - (prefix * 0.1 * (1 - jaro_similarity) + jaro_similarity)
}

# usage: 
#    sidef script.sf < unixdict.txt

var words = ARGF.slurp.words

%w(accomodate definately goverment occured publically recieve seperate untill wich).each {|word|

   var result = Hash(words.map { (_, jaro_winkler_distance(word, _)) }...)

   say "\nClosest 5 dictionary words with a Jaro-Winkler distance < .15 from #{word}:"
   result.grep {|_,v| v < .15 }.sort_by{|_,v| v }.head(5).each_2d {|k,v|
        printf("%15s : %0.4f\n", k, v)
    }
}
```

#### Output:
```
Closest 5 dictionary words with a Jaro-Winkler distance < .15 from accomodate:
    accommodate : 0.0182
      accordant : 0.1044
       accolade : 0.1136
      acclimate : 0.1219
    accompanist : 0.1327

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from definately:
         define : 0.0800
       definite : 0.0850
        defiant : 0.0886
     definitive : 0.1200
        deflate : 0.1267

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from goverment:
         govern : 0.0667
       governor : 0.1167
      governess : 0.1175
     governance : 0.1330
           goer : 0.1481

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from occured:
       occurred : 0.0250
          occur : 0.0571
      occurrent : 0.0952
        occlude : 0.1056
      concurred : 0.1217

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from publically:
         public : 0.0800
    publication : 0.1327

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from recieve:
        receive : 0.0333
          reeve : 0.0762
        relieve : 0.0762
      recessive : 0.0852
      receptive : 0.0852

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from seperate:
      desperate : 0.0787
       separate : 0.0917
      temperate : 0.1157
           sept : 0.1167
        septate : 0.1306

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from untill:
          until : 0.0333
           till : 0.1111
     huntsville : 0.1333
         unital : 0.1422

Closest 5 dictionary words with a Jaro-Winkler distance < .15 from wich:
          witch : 0.0533
          winch : 0.0533
          which : 0.0600
        wichita : 0.0857
         twitch : 0.1111
```
