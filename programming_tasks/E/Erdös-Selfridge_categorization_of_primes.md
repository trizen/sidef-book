[1]: https://rosettacode.org/wiki/Erdös-Selfridge_categorization_of_primes

# [Erdös-Selfridge categorization of primes][1]

```ruby
func Erdös_Selfridge_class(n, s=1) is cached {
    var f = factor_exp(n+s)
    f.last.head > 3 || return 1
    f.map {|p| __FUNC__(p.head, s) }.max + 1
}
 
say "First two hundred primes; Erdös-Selfridge categorized:"
200.pn_primes.group_by(Erdös_Selfridge_class).sort_by{.to_i}.each_2d {|k,v|
    say "#{k} => #{v}"
}
 
say "\nSummary of first 10^6 primes; Erdös-Selfridge categorized:";
1e6.pn_primes.group_by(Erdös_Selfridge_class).sort_by{.to_i}.each_2d {|k,v|
    printf("Category %2d: first: %9s  last: %10s  count: %s\n", k, v.first, v.last, v.len)
}
```

#### Output:
```
First two hundred primes; Erdös-Selfridge categorized:
1 => [2, 3, 5, 7, 11, 17, 23, 31, 47, 53, 71, 107, 127, 191, 383, 431, 647, 863, 971, 1151]
2 => [13, 19, 29, 41, 43, 59, 61, 67, 79, 83, 89, 97, 101, 109, 131, 137, 139, 149, 167, 179, 197, 199, 211, 223, 229, 239, 241, 251, 263, 269, 271, 281, 283, 293, 307, 317, 349, 359, 367, 373, 419, 433, 439, 449, 461, 479, 499, 503, 509, 557, 563, 577, 587, 593, 599, 619, 641, 643, 659, 709, 719, 743, 751, 761, 769, 809, 827, 839, 881, 919, 929, 953, 967, 991, 1019, 1033, 1049, 1069, 1087, 1103, 1187, 1223]
3 => [37, 103, 113, 151, 157, 163, 173, 181, 193, 227, 233, 257, 277, 311, 331, 337, 347, 353, 379, 389, 397, 401, 409, 421, 457, 463, 467, 487, 491, 521, 523, 541, 547, 569, 571, 601, 607, 613, 631, 653, 683, 701, 727, 733, 773, 787, 797, 811, 821, 829, 853, 857, 859, 877, 883, 911, 937, 947, 983, 997, 1009, 1013, 1031, 1039, 1051, 1061, 1063, 1091, 1097, 1117, 1123, 1153, 1163, 1171, 1181, 1193, 1217]
4 => [73, 313, 443, 617, 661, 673, 677, 691, 739, 757, 823, 887, 907, 941, 977, 1093, 1109, 1129, 1201, 1213]
5 => [1021]

Summary of first 10^6 primes; Erdös-Selfridge categorized:
Category  1: first:         2  last:   10616831  count: 46
Category  2: first:        13  last:   15482669  count: 10497
Category  3: first:        37  last:   15485863  count: 201987
Category  4: first:        73  last:   15485849  count: 413891
Category  5: first:      1021  last:   15485837  count: 263109
Category  6: first:      2917  last:   15485857  count: 87560
Category  7: first:     15013  last:   15484631  count: 19389
Category  8: first:     49681  last:   15485621  count: 3129
Category  9: first:    532801  last:   15472811  count: 363
Category 10: first:   1065601  last:   15472321  count: 28
Category 11: first:   8524807  last:    8524807  count: 1
```
