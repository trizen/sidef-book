[1]: https://rosettacode.org/wiki/Esthetic_numbers

# [Esthetic numbers][1]

```ruby
func generate_esthetic(root, upto, callback, b=10) {
 
    var v = root.digits2num(b)
 
    if (v > upto) {
        return nil
    }
 
    callback(v)
 
    var t = root.head
 
    __FUNC__([t+1, root...], upto, callback, b) if (t+1  < b)
    __FUNC__([t-1, root...], upto, callback, b) if (t-1 >= 0)
}
 
func upto_esthetic(upto, b=10) {
    gather {
        for k in (1..^b) {
            generate_esthetic([k], upto, { take(_) }, b)
        }
    }.sort
}
 
func first_n_esthetic(n, b=10) {
 
    var m = n**2
 
    loop {
        var list = upto_esthetic(m, b)
        return list.first(n) if (list.len >= n)
        m *= b
    }
}
 
for b in (2..16) {
    say "\n#{b}-esthetic numbers with indices #{4*b}..#{6*b}: "
    say first_n_esthetic(6*b, b).last(6*b - 4*b + 1).map{.base(b)}.join(' ')
}
 
say "\nBase 10 esthetic numbers between 1,000 and 9,999:"
upto_esthetic(9_999).grep { _ > 1_000 }.slices(20).each { .join(' ').say }
 
say "\nBase 10 esthetic numbers between 100,000,000 and 130,000,000:"
upto_esthetic(13e7).grep { _ > 1e8 }.slices(9).each { .join(' ').say }
```

#### Output:
```
2-esthetic numbers with indices 8..12: 
10101010 101010101 1010101010 10101010101 101010101010

3-esthetic numbers with indices 12..18: 
1210 1212 2101 2121 10101 10121 12101

4-esthetic numbers with indices 16..24: 
323 1010 1012 1210 1212 1232 2101 2121 2123

5-esthetic numbers with indices 20..30: 
323 343 432 434 1010 1012 1210 1212 1232 1234 2101

6-esthetic numbers with indices 24..36: 
343 345 432 434 454 543 545 1010 1012 1210 1212 1232 1234

7-esthetic numbers with indices 28..42: 
345 432 434 454 456 543 545 565 654 656 1010 1012 1210 1212 1232

8-esthetic numbers with indices 32..48: 
432 434 454 456 543 545 565 567 654 656 676 765 767 1010 1012 1210 1212

9-esthetic numbers with indices 36..54: 
434 454 456 543 545 565 567 654 656 676 678 765 767 787 876 878 1010 1012 1210

10-esthetic numbers with indices 40..60: 
454 456 543 545 565 567 654 656 676 678 765 767 787 789 876 878 898 987 989 1010 1012

11-esthetic numbers with indices 44..66: 
456 543 545 565 567 654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 a98 a9a 1010

12-esthetic numbers with indices 48..72: 
543 545 565 567 654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 9ab a98 a9a aba ba9 bab

13-esthetic numbers with indices 52..78: 
545 565 567 654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 9ab a98 a9a aba abc ba9 bab bcb cba

14-esthetic numbers with indices 56..84: 
565 567 654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 9ab a98 a9a aba abc ba9 bab bcb bcd cba cbc cdc

15-esthetic numbers with indices 60..90: 
567 654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 9ab a98 a9a aba abc ba9 bab bcb bcd cba cbc cdc cde dcb dcd

16-esthetic numbers with indices 64..96: 
654 656 676 678 765 767 787 789 876 878 898 89a 987 989 9a9 9ab a98 a9a aba abc ba9 bab bcb bcd cba cbc cdc cde dcb dcd ded def edc

Base 10 esthetic numbers between 1,000 and 9,999:
1010 1012 1210 1212 1232 1234 2101 2121 2123 2321 2323 2343 2345 3210 3212 3232 3234 3432 3434 3454
3456 4321 4323 4343 4345 4543 4545 4565 4567 5432 5434 5454 5456 5654 5656 5676 5678 6543 6545 6565
6567 6765 6767 6787 6789 7654 7656 7676 7678 7876 7878 7898 8765 8767 8787 8789 8987 8989 9876 9878
9898

Base 10 esthetic numbers between 100,000,000 and 130,000,000:
101010101 101010121 101010123 101012101 101012121 101012123 101012321 101012323 101012343
101012345 101210101 101210121 101210123 101212101 101212121 101212123 101212321 101212323
101212343 101212345 101232101 101232121 101232123 101232321 101232323 101232343 101232345
101234321 101234323 101234343 101234345 101234543 101234545 101234565 101234567 121010101
121010121 121010123 121012101 121012121 121012123 121012321 121012323 121012343 121012345
121210101 121210121 121210123 121212101 121212121 121212123 121212321 121212323 121212343
121212345 121232101 121232121 121232123 121232321 121232323 121232343 121232345 121234321
121234323 121234343 121234345 121234543 121234545 121234565 121234567 123210101 123210121
123210123 123212101 123212121 123212123 123212321 123212323 123212343 123212345 123232101
123232121 123232123 123232321 123232323 123232343 123232345 123234321 123234323 123234343
123234345 123234543 123234545 123234565 123234567 123432101 123432121 123432123 123432321
123432323 123432343 123432345 123434321 123434323 123434343 123434345 123434543 123434545
123434565 123434567 123454321 123454323 123454343 123454345 123454543 123454545 123454565
123454567 123456543 123456545 123456565 123456567 123456765 123456767 123456787 123456789
```