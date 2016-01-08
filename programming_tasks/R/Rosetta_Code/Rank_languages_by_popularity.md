[1]: http://rosettacode.org/wiki/Rosetta_Code/Rank_languages_by_popularity

# [Rosetta Code/Rank languages by popularity][1]

```ruby
require 'MediaWiki::API';

var api = %s'MediaWiki::API'.new(
    Hash.new(api_url => 'http://rosettacode.org/mw/api.php')
);

var languages = [];
var gcmcontinue;
loop {
    var apih = api.api(
        Hash.new(
            action      => 'query',
            generator   => 'categorymembers',
            gcmtitle    => 'Category:Programming Languages',
            gcmlimit    => 250,
            prop        => 'categoryinfo',
            gcmcontinue => gcmcontinue,
        )
    );

    languages.append(apih{:query}{:pages}.values...);
    gcmcontinue = apih{'continue'}{:gcmcontinue};
    gcmcontinue || break;
}

languages.each { |lang|
    lang{:title} -= /^Category:/;
    lang{:categoryinfo}{:size} := 0;
}

var sorted_languages = languages.sort_by { |lang|
    -lang{:categoryinfo}{:size}
}

sorted_languages.each_kv { |i, lang|
    printf("%3d. %20s - %3d\n", i+1, lang{:title}, lang{:categoryinfo}{:size});
}
```

#### Output:
```
  1.               Racket - 903
  2.                  Tcl - 897
  3.               Python - 865
  4.                    J - 821
  5.               Perl 6 - 797
  6.                 Ruby - 783
  7.                    C - 767
  8.                   Go - 755
  9.                    D - 745
 10.                 REXX - 725
 11.                 Perl - 724
 12.              Haskell - 700
 13.             PicoLisp - 699
 14.          Mathematica - 687
 15.                  Zkl - 675
 16.                 Java - 662
 17.                  Ada - 629
 18.           AutoHotkey - 606
 19.                  C++ - 596
 20.               Unicon - 581
 21.          Common Lisp - 571
 22.                Scala - 560
 23.                Sidef - 555
...
```
