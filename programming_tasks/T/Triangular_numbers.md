[1]: https://rosettacode.org/wiki/Triangular_numbers

# [Triangular numbers][1]

```ruby
func pentatopic_root(x) {
    (sqrt(5 + 4*sqrt(24*x + 1)) - 3)/2
}

func polytopic (r, range) {
    range.map {|n| binomial(n + r - 1, r) }
}

[
    2, 'triangular', 3, 'tetrahedral', 4, 'pentatopic', 12, '12-simplex'
].slices(2).each_2d {|r,label|
    say "\nFirst 30 #{label} numbers:"
    polytopic(r, ^30).slices(6).each{.join(' ').say}
}

for n in (7140, 21408696, 26728085384, 14545501785001) {
    printf ("\nRoots of #{n}:
   triangular-root: %s
  tetrahedral-root: %s
   pentatopic-root: %s\n",
        polygonal_root(n,3), pyramidal_root(n,3), pentatopic_root(n))
}
```

#### Output:
```
First 30 triangular numbers:
0 1 3 6 10 15
21 28 36 45 55 66
78 91 105 120 136 153
171 190 210 231 253 276
300 325 351 378 406 435

First 30 tetrahedral numbers:
0 1 4 10 20 35
56 84 120 165 220 286
364 455 560 680 816 969
1140 1330 1540 1771 2024 2300
2600 2925 3276 3654 4060 4495

First 30 pentatopic numbers:
0 1 5 15 35 70
126 210 330 495 715 1001
1365 1820 2380 3060 3876 4845
5985 7315 8855 10626 12650 14950
17550 20475 23751 27405 31465 35960

First 30 12-simplex numbers:
0 1 13 91 455 1820
6188 18564 50388 125970 293930 646646
1352078 2704156 5200300 9657700 17383860 30421755
51895935 86493225 141120525 225792840 354817320 548354040
834451800 1251677700 1852482996 2707475148 3910797436 5586853480

Roots of 7140:
   triangular-root: 119
  tetrahedral-root: 34
   pentatopic-root: 18.8766466159280066079017828266675662291603339398

Roots of 21408696:
   triangular-root: 6543
  tetrahedral-root: 503.56182697463651404819613028417773405650502954
   pentatopic-root: 149.060947375265867484387574884713368069543117436

Roots of 26728085384:
   triangular-root: 231205.405565255836957291031960694122304324644392
  tetrahedral-root: 5432
   pentatopic-root: 893.442456751684869888466211529245370387840101701

Roots of 14545501785001:
   triangular-root: 5393607.1581451723164973047246554846079685622181
  tetrahedral-root: 44355.7773840732560526209168894228874431786835756
   pentatopic-root: 4321
```
