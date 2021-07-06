[1]: https://rosettacode.org/wiki/Coprime_triplets

# [Coprime triplets][1]

```ruby
func coprime_triplets(callback) {
 
    var (
        list = [1,2],
        a = 1,
        b = 2,
        k = 3,
        seen = Set()
    )
 
    loop {
        for (var n = k; true; ++n) {
            if (!seen.has(n) && is_coprime(n, a) && is_coprime(n, b)) {
 
                list << n
                seen << n
 
                callback(list) && return list
 
                (a, b) = (b, n)
 
                while (seen.has(k)) {
                    seen.remove(k++)
                }
 
                break
            }
        }
    }
}
 
say "Coprime triplets before first term is > 50:"
coprime_triplets({|list|
    list.tail >= 50
}).first(-1).slices(10).each { .«%« '%4d' -> join(' ').say }
 
say "\nLeast Coprime triplets that encompass 1 through 50:"
coprime_triplets({|list|
    list.sort.first(50) == @(1..50)
}).slices(10).each { .«%« '%4d' -> join(' ').say }
 
say "\n1001st through 1050th Coprime triplet:"
coprime_triplets({|list|
    list.len == 1050
}).last(50).slices(10).each { .«%« '%4d' -> join(' ').say }
```

#### Output:
```
Coprime triplets before first term is > 50:
   1    2    3    5    4    7    9    8   11   13
   6   17   19   10   21   23   16   15   29   14
  25   27   22   31   35   12   37   41   18   43
  47   20   33   49   26   45

Least Coprime triplets that encompass 1 through 50:
   1    2    3    5    4    7    9    8   11   13
   6   17   19   10   21   23   16   15   29   14
  25   27   22   31   35   12   37   41   18   43
  47   20   33   49   26   45   53   28   39   55
  32   51   59   38   61   63   34   65   57   44
  67   69   40   71   73   24   77   79   30   83
  89   36   85   91   46   75   97   52   81   95
  56   87  101   50   93  103   58   99  107   62
 105  109   64  111  113   68  115  117   74  119
 121   48  125  127   42

1001st through 1050th Coprime triplet:
 682 1293 1361  680 1287 1363  686 1299 1367  688
1305 1369  692 1311 1373  694 1317 1375  698 1323
1381  704 1329 1379  706 1335 1387  716 1341 1385
 712 1347 1391  700 1353 1399  710 1359 1393  718
1371 1397  722 1365 1403  724 1377 1405  728 1383
```
