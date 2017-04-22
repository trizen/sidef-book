[1]: http://rosettacode.org/wiki/Rosetta_Code/Rank_languages_by_popularity

# [Rosetta Code/Rank languages by popularity][1]

```ruby
require('MediaWiki::API')

var api = %O<MediaWiki::API>.new(
    Hash(api_url => 'http://rosettacode.org/mw/api.php')
)

var languages = []
var gcmcontinue
loop {
    var apih = api.api(
        Hash(
            action      => 'query',
            generator   => 'categorymembers',
            gcmtitle    => 'Category:Programming Languages',
            gcmlimit    => 250,
            prop        => 'categoryinfo',
            gcmcontinue => gcmcontinue,
        )
    )

    languages.append(apih{:query}{:pages}.values...)
    gcmcontinue = apih{:continue}{:gcmcontinue}
    gcmcontinue || break
}

languages.each { |lang|
    lang{:title} -= /^Category:/
    lang{:categoryinfo}{:size} := 0
}

var sorted_languages = languages.sort_by { |lang|
    -lang{:categoryinfo}{:size}
}

sorted_languages.each_kv { |i, lang|
    printf("%3d. %20s - %3d\n", i+1, lang{:title}, lang{:categoryinfo}{:size})
}
```

#### Output:
```
  1.               Racket - 938
  2.               Python - 930
  3.                  Tcl - 904
  4.               Perl 6 - 877
  5.                    J - 863
  6.                  Zkl - 834
  7.                 Ruby - 830
  8.                    C - 805
  9.                   Go - 793
 10.              Haskell - 785
 11.                 Java - 783
 12.                 REXX - 776
 13.                 Perl - 765
 14.                    D - 753
 15.             PicoLisp - 731
 16.          Mathematica - 702
 17.                Sidef - 696
...
```
