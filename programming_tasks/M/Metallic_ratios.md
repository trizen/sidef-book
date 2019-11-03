[1]: https://rosettacode.org/wiki/Metallic_ratios

# [Metallic ratios][1]

```ruby
func seqRatio(f, places = 32) {
    1..Inf -> reduce {|t,n|
        var r = (f(n+1)/f(n)).round(-places)
        return(n, r.as_dec(places + r.abs.int.len)) if (r == t)
        r
    }
}
 
for k,v in (%w(Platinum Golden Silver Bronze Copper Nickel Aluminum Iron Tin Lead).kv) {
    next if (k == 0)   # undefined ratio
    say "Lucas sequence U_n(#{k},-1) for #{v} ratio"
    var f = {|n| lucasu(k, -1, n) }
    say ("First 15 elements: ", 15.of(f).join(', '))
    var (n, r) = seqRatio(f)
    say "Approximated value: #{r} reached after #{n} iterations"
    say ''
}
 
with (seqRatio({|n| fib(n) }, 256)) {|n,v|
    say "Golden ratio to 256 decimal places:"
    say "Approximated value: #{v}"
    say "Reached after #{n} iterations"
}
```

#### Output:
```
Lucas sequence U_n(1,-1) for Golden ratio
First 15 elements: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377
Approximated value: 1.61803398874989484820458683436564 reached after 79 iterations

Lucas sequence U_n(2,-1) for Silver ratio
First 15 elements: 0, 1, 2, 5, 12, 29, 70, 169, 408, 985, 2378, 5741, 13860, 33461, 80782
Approximated value: 2.4142135623730950488016887242097 reached after 45 iterations

Lucas sequence U_n(3,-1) for Bronze ratio
First 15 elements: 0, 1, 3, 10, 33, 109, 360, 1189, 3927, 12970, 42837, 141481, 467280, 1543321, 5097243
Approximated value: 3.30277563773199464655961063373525 reached after 33 iterations

Lucas sequence U_n(4,-1) for Copper ratio
First 15 elements: 0, 1, 4, 17, 72, 305, 1292, 5473, 23184, 98209, 416020, 1762289, 7465176, 31622993, 133957148
Approximated value: 4.23606797749978969640917366873128 reached after 28 iterations

Lucas sequence U_n(5,-1) for Nickel ratio
First 15 elements: 0, 1, 5, 26, 135, 701, 3640, 18901, 98145, 509626, 2646275, 13741001, 71351280, 370497401, 1923838285
Approximated value: 5.19258240356725201562535524577016 reached after 26 iterations

Lucas sequence U_n(6,-1) for Aluminum ratio
First 15 elements: 0, 1, 6, 37, 228, 1405, 8658, 53353, 328776, 2026009, 12484830, 76934989, 474094764, 2921503573, 18003116202
Approximated value: 6.16227766016837933199889354443272 reached after 23 iterations

Lucas sequence U_n(7,-1) for Iron ratio
First 15 elements: 0, 1, 7, 50, 357, 2549, 18200, 129949, 927843, 6624850, 47301793, 337737401, 2411463600, 17217982601, 122937341807
Approximated value: 7.14005494464025913554865124576352 reached after 21 iterations

Lucas sequence U_n(8,-1) for Tin ratio
First 15 elements: 0, 1, 8, 65, 528, 4289, 34840, 283009, 2298912, 18674305, 151693352, 1232221121, 10009462320, 81307919681, 660472819768
Approximated value: 8.12310562561766054982140985597408 reached after 20 iterations

Lucas sequence U_n(9,-1) for Lead ratio
First 15 elements: 0, 1, 9, 82, 747, 6805, 61992, 564733, 5144589, 46866034, 426938895, 3889316089, 35430783696, 322766369353, 2940328107873
Approximated value: 9.1097722286464436550011371408814 reached after 19 iterations

Golden ratio to 256 decimal places:
Approximated value: 1.6180339887498948482045868343656381177203091798057628621354486227052604628189024497072072041893911374847540880753868917521266338622235369317931800607667263544333890865959395829056383226613199282902678806752087668925017116962070322210432162695486262963136144
Reached after 616 iterations
```
