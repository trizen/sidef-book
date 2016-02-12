[1]: http://rosettacode.org/wiki/Convert_seconds_to_compound_duration

# [Convert seconds to compound duration][1]

```ruby
func polymod(n, *divs) {
    gather {
        divs.each { |i|
            var m = take(n % i)
            (n -= m) /= i
        }
        take(n)
    }
}
 
func compound_duration(seconds) {
    (polymod(seconds, 60, 60, 24, 7) ~Z <sec min hr d wk>).grep { |a|
        a[0] > 0
    }.reverse.map{.join(' ')}.join(', ')
}
 
[7259, 86400, 6000000].each { |s|
    say "#{'%7d' % s} sec  =  #{compound_duration(s)}"
}
```

#### Output:
```
   7259 sec  =  2 hr, 59 sec
  86400 sec  =  1 d
6000000 sec  =  9 wk, 6 d, 10 hr, 40 min
```