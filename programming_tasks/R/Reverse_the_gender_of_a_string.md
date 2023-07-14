[1]: https://rosettacode.org/wiki/Reverse_the_gender_of_a_string

# [Reverse the gender of a string][1]

```ruby
var male2female = <<'EOD'
  maleS femaleS, maleness femaleness, him her, himself herself, his her, his
  hers, he she, Mr Mrs, Mister Missus, Ms Mr, Master Miss, MasterS MistressES,
  uncleS auntS, nephewS nieceS, sonS daughterS, grandsonS granddaughterS,
  brotherS sisterS, man woman, men women, boyS girlS, paternal maternal,
  grandfatherS grandmotherS, GodfatherS GodmotherS, GodsonS GoddaughterS,
  fiancéS fiancéeS, husband wife, husbands wives, fatherS motherS, bachelorS
  spinsterS, bridegroomS brideS, widowerS widowS, KnightS DameS, Sir DameS,
  KingS QueenS, DukeS DuchessES, PrinceS PrincessES, Lord Lady, Lords Ladies,
  MarquessES MarchionessES, EarlS CountessES, ViscountS ViscountessES, ladS
  lassES, sir madam, gentleman lady, gentlemen ladies, BaronS BaronessES,
  stallionS mareS, ramS eweS, coltS fillieS, billy nanny, billies nannies,
  bullS cowS, godS goddessES, heroS heroineS, shirtS blouseS, undies nickers,
  sweat glow, jackarooS jillarooS, gigoloS hookerS, landlord landlady,
  landlords landladies, manservantS maidservantS, actorS actressES, CountS
  CountessES, EmperorS EmpressES, giantS giantessES, heirS heiressES, hostS
  hostessES, lionS lionessES, managerS manageressES, murdererS murderessES,
  priestS priestessES, poetS poetessES, shepherdS shepherdessES, stewardS
  stewardessES, tigerS tigressES, waiterS waitressES, cockS henS, dogS bitchES,
  drakeS henS, dogS vixenS, tomS tibS, boarS sowS, buckS roeS, peacockS
  peahenS, gander goose, ganders geese, friarS nunS, monkS nunS
EOD
 
var m2f = male2female.split(/,\s*/).map { |tok| tok.words}
 
var re_plural = /E?S\z/
var re_ES = /ES\z/
 
func gen_pluralize(m, f) {
    [
        [m - re_plural, f - re_plural],
        [m.sub(re_ES, 'es'), f.sub(re_ES, 'es')],
        [m.sub(re_plural, 's'), f.sub(re_plural, 's')],
    ]
}
 
var dict = Hash()
 
for m,f in m2f {
    for x,y in gen_pluralize(m, f).map{.map{.lc}} {
        if (x ~~ dict) {
            dict{y} = x
        } else {
            dict{x, y} = (y, x)
        }
    }
}
 
var gen_re = Regex('\b(' + dict.keys.join('|') + ')\b', 'i')
 
func copy_case(orig, repl) {
    var a = orig.chars
    var b = repl.chars
 
    var uc = 0
    var min = [a, b].map{.len}.min
    for i in ^min {
        if (a[i] ~~ /^[[:upper:]]/) {
            b[i].uc!
            ++uc
        }
    }
 
    uc == min ? repl.uc : b.join('')
}
 
func reverse_gender(text) {
    text.gsub(gen_re, { |a| copy_case(a, dict{a.lc}) })
}
```


Example:

```ruby
say reverse_gender("She was a soul stripper. She took my heart!")
```

#### Output:
```
He was a soul stripper. He took my heart!
```
