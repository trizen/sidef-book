[1]: https://rosettacode.org/wiki/Cyclops_numbers

# [Cyclops numbers][1]

```ruby
func cyclops_numbers(base = 10) {
    Enumerator({|callback|
 
        var digits = @(1 .. base-1)
 
        for k in (0 .. Inf `by` 2) {
            digits.variations_with_repetition(k, {|*a|
                a = (a.first(a.len>>1) + [0] + a.last(a.len>>1))
                callback(a.flip.digits2num(base))
            })
        }
    })
}
 
func palindromic_cyclops_numbers(base = 10) {
    Enumerator({|callback|
 
        var digits = @(1 .. base-1)
 
        for k in (0..Inf) {
            digits.variations_with_repetition(k, {|*a|
                a = (a + [0] + a.flip)
                callback(a.flip.digits2num(base))
            })
        }
    })
}
 
func prime_cyclops(base = 10) {
    var iter = cyclops_numbers(base)
    Enumerator({|callback|
        iter.each {|n|
            callback(n) if n.is_prime
        }
    })
}
 
func blind_prime_cyclops(base = 10) {
    var iter = prime_cyclops(base)
    Enumerator({|callback|
        iter.each {|n|
            var k = (n.len(base)-1)>>1
            var r = ipow(base, k)
            if (r*idiv(n, r*base) + n%r -> is_prime) {
                callback(n)
            }
        }
    })
}
 
func palindromic_prime_cyclops(base = 10) {
    var iter = palindromic_cyclops_numbers(base)
    Enumerator({|callback|
        iter.each {|n|
            callback(n) if n.is_prime
        }
    })
}
 
for text,f in ([
    ['', cyclops_numbers],
    ['prime', prime_cyclops],
    ['blind prime', blind_prime_cyclops],
    ['palindromic prime', palindromic_prime_cyclops],
]) {
 
    with (50) {|k|
        say "First #{k} #{text} cyclops numbers:"
        f().first(k).each_slice(10, {|*a|
            a.map { '%7s' % _ }.join(' ').say
        })
    }
 
    var min = 10_000_000
    var iter = f()
    var index = 0
    var arr = Enumerator({|callback|
        iter.each {|n|
            callback([index, n]) if (n > min)
            ++index
        }
    }).first(1)[0]
    say "\nFirst #{text} term > #{min.commify}: #{arr[1].commify} at (zero based) index: #{arr[0].commify}\n"
}
```

#### Output:
```
First 50  cyclops numbers:
      0     101     102     103     104     105     106     107     108     109
    201     202     203     204     205     206     207     208     209     301
    302     303     304     305     306     307     308     309     401     402
    403     404     405     406     407     408     409     501     502     503
    504     505     506     507     508     509     601     602     603     604

First  term > 10,000,000: 111,101,111 at (zero based) index: 538,084

First 50 prime cyclops numbers:
    101     103     107     109     307     401     409     503     509     601
    607     701     709     809     907   11027   11047   11057   11059   11069
  11071   11083   11087   11093   12011   12037   12041   12043   12049   12071
  12073   12097   13033   13037   13043   13049   13063   13093   13099   14011
  14029   14033   14051   14057   14071   14081   14083   14087   15013   15017

First prime term > 10,000,000: 111,101,129 at (zero based) index: 39,319

First 50 blind prime cyclops numbers:
    101     103     107     109     307     401     503     509     601     607
    701     709     809     907   11071   11087   11093   12037   12049   12097
  13099   14029   14033   14051   14071   14081   14083   14087   15031   15053
  15083   16057   16063   16067   16069   16097   17021   17033   17041   17047
  17053   17077   18047   18061   18077   18089   19013   19031   19051   19073

First blind prime term > 10,000,000: 111,101,161 at (zero based) index: 11,393

First 50 palindromic prime cyclops numbers:
    101   16061   31013   35053   38083   73037   74047   91019   94049 1120211
1150511 1160611 1180811 1190911 1250521 1280821 1360631 1390931 1490941 1520251
1550551 1580851 1630361 1640461 1660661 1670761 1730371 1820281 1880881 1930391
1970791 3140413 3160613 3260623 3310133 3380833 3460643 3470743 3590953 3670763
3680863 3970793 7190917 7250527 7310137 7540457 7630367 7690967 7750577 7820287

First palindromic prime term > 10,000,000: 114,808,411 at (zero based) index: 66
```
