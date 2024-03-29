[1]: https://rosettacode.org/wiki/Stable_marriage_problem

# [Stable marriage problem][1]

```ruby
var he_likes = Hash(
    abe  => < abi eve cath ivy jan dee fay bea hope gay >,
    bob  => < cath hope abi dee eve fay bea jan ivy gay >,
    col  => < hope eve abi dee bea fay ivy gay cath jan >,
    dan  => < ivy fay dee gay hope eve jan bea cath abi >,
    ed   => < jan dee bea cath fay eve abi ivy hope gay >,
    fred => < bea abi dee gay eve ivy cath jan hope fay >,
    gav  => < gay eve ivy bea cath abi dee hope jan fay >,
    hal  => < abi eve hope fay ivy cath jan bea gay dee >,
    ian  => < hope cath dee gay bea abi fay ivy jan eve >,
    jon  => < abi fay jan gay eve bea dee cath ivy hope >,
);
 
var she_likes = Hash(
    abi  => < bob fred jon gav ian abe dan ed col hal >,
    bea  => < bob abe col fred gav dan ian ed jon hal >,
    cath => < fred bob ed gav hal col ian abe dan jon >,
    dee  => < fred jon col abe ian hal gav dan bob ed >,
    eve  => < jon hal fred dan abe gav col ed ian bob >,
    fay  => < bob abe ed ian jon dan fred gav col hal >,
    gay  => < jon gav hal fred bob abe col ed dan ian >,
    hope => < gav jon bob abe ian dan hal ed col fred >,
    ivy  => < ian col hal gav fred bob abe ed jon dan >,
    jan  => < ed hal gav abe bob jon col ian fred dan >,
);
 
var guys = he_likes.keys;
var gals = she_likes.keys;
 
var (:fiancé, :fiancée, :proposed);
 
func she_prefers (her, hottie) { var a = she_likes{her}; a.index(hottie) < a.index(fiancé{her}) }
func he_prefers  (him, hottie) { var a =  he_likes{him}; a.index(hottie) < a.index(fiancée{him}) }
 
func unmatched_guy { guys.first {|k| !defined fiancée{k} } }
func preferred_choice(guy) { he_likes{guy}.first {|k| !defined proposed{guy}{k} } }
 
func engage(guy, gal) {
    fiancé{gal} = guy;
    fiancée{guy} = gal;
}
 
func match_em {
    say 'Matchmaking:';
    while (defined(var guy = unmatched_guy())) {
        var gal = preferred_choice(guy);
        proposed{guy}{gal} = '❤';
        if (!defined fiancé{gal}) {
            engage(guy, gal);
            say "\t#{gal} and #{guy}";
        }
        elsif (she_prefers(gal, guy)) {
            var engaged_guy = fiancé{gal};
            engage(guy, gal);
            fiancée{engaged_guy} = nil;
            say "\t#{gal} dumped #{engaged_guy} for #{guy}";
        }
    }
}
 
func check_stability {
    var instabilities = gather {
        guys.each { |m|
            gals.each { |w|
                if (he_prefers(m, w) && she_prefers(w, m)) {
                    take "\t#{w} prefers #{m} to #{fiancé{w}} and #{m} prefers #{w} to #{fiancée{m}}";
                }
            }
        }
    }
 
    say 'Stablility:';
    instabilities.is_empty
        ? say "\t(all marriages stable)"
        : instabilities.each { |i| say i };
}
 
func perturb_em {
    say 'Perturb:';
    say "\tengage abi with fred and bea with jon";
    engage('fred', 'abi');
    engage('jon', 'bea');
}
 
match_em();
check_stability();
 
perturb_em();
check_stability();
```

#### Output:
```
Matchmaking:
        abi and jon
        eve and abe
        bea and fred
        cath and bob
        hope and ian
        eve dumped abe for hal
        ivy and abe
        dee and col
        jan and ed
        fay and dan
        gay and gav
Stablility:
        (all marriages stable)
Perturb:
        engage abi with fred and bea with jon
Stablility:
        gay prefers jon to gav and jon prefers gay to bea
        eve prefers jon to hal and jon prefers eve to bea
        fay prefers jon to dan and jon prefers fay to bea
        bea prefers fred to jon and fred prefers bea to abi
```