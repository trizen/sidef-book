[1]: http://rosettacode.org/wiki/Rosetta_Code/Rank_languages_by_popularity

# [Rosetta Code/Rank languages by popularity][1]

```ruby
require('MediaWiki::API')

var api = %s<MediaWiki::API>.new(
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
  1.               Racket - 904
  2.                  Tcl - 897
  3.               Python - 867
  4.                    J - 829
  5.               Perl 6 - 800
  6.                 Ruby - 789
  7.                    C - 772
  8.                   Go - 756
  9.                    D - 745
 10.                 Perl - 730
 11.                 REXX - 725
 12.              Haskell - 704
 13.             PicoLisp - 699
 14.          Mathematica - 689
 15.                  Zkl - 683
 16.                 Java - 663
 17.                  Ada - 629
 18.           AutoHotkey - 606
 19.                  C++ - 599
 20.                Sidef - 588
...
```
