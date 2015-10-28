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
    gcmcontinue = apih{'query-continue'}{:categorymembers}{:gcmcontinue};
    gcmcontinue || break;
}
 
languages.each { |lang|
    lang{:title} -= /^Category:/;
    lang{:categoryinfo}{:size} \\= 0;
}
 
var sorted_languages = languages.sort { |a, b|
    a{:categoryinfo}{:size} <=> b{:categoryinfo}{:size}
}.reverse;
 
sorted_languages.each_with_index { |i, lang|
    printf("%3d. %20s - %3d\n", i+1, lang{:title}, lang{:categoryinfo}{:size});
}
```

#### Output:
```
  1.                  Tcl - 889
  2.               Racket - 877
  3.               Python - 856
  4.                    J - 806
  5.                 Ruby - 775
  6.               Perl 6 - 767
  7.                    C - 759
  8.                   Go - 747
  9.                    D - 740
 10.                 Perl - 712
 11.                 REXX - 706
 12.             PicoLisp - 695
 13.              Haskell - 690
 14.          Mathematica - 675
 15.                  Zkl - 656
 16.                 Java - 654
 17.                  Ada - 624
 18.           AutoHotkey - 591
 19.               Unicon - 581
 20.                  C++ - 575
 21.          Common Lisp - 556
 22.                Scala - 550
 23.            BBC BASIC - 532
 24.                 Icon - 523
 25.              C sharp - 517
 26.                OCaml - 508
 27.                  Nim - 502
 28.            PureBasic - 491
 29.              Clojure - 488
 30.               Erlang - 458
 31.              PARI/GP - 446
 32.           JavaScript - 444
 33.                Julia - 413
 34.                   Jq - 412
 35.                Sidef - 411
...
```