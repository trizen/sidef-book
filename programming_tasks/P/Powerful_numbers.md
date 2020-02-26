[1]: https://rosettacode.org/wiki/Powerful_numbers

# [Powerful numbers][1]

### Generation

```ruby
func powerful(n, k=2) {
 
    var list = []
 
    func (m,r) {
        if (r < k) {
            list << m
            return nil
        }
        for a in (1 .. iroot(idiv(n,m), r)) {
            if (r > k) {
                a.is_coprime(m) || next
                a.is_squarefree || next
            }
            __FUNC__(m * a**r, r-1)
        }
    }(1, 2*k - 1)
 
    return list.sort
}
 
for k in (2..10) {
    var a = powerful(10**k, k)
    var h = a.head(5).join(', ')
    var t = a.tail(5).join(', ')
    printf("For k=%-2d there are %d k-powerful numbers <= 10^k: [%s, ..., %s]\n", k, a.len, h, t)
}
```

#### Output:
```
For k=2  there are 14 k-powerful numbers <= 10^k: [1, 4, 8, 9, 16, ..., 49, 64, 72, 81, 100]
For k=3  there are 20 k-powerful numbers <= 10^k: [1, 8, 16, 27, 32, ..., 625, 648, 729, 864, 1000]
For k=4  there are 25 k-powerful numbers <= 10^k: [1, 16, 32, 64, 81, ..., 5184, 6561, 7776, 8192, 10000]
For k=5  there are 32 k-powerful numbers <= 10^k: [1, 32, 64, 128, 243, ..., 65536, 69984, 78125, 93312, 100000]
For k=6  there are 38 k-powerful numbers <= 10^k: [1, 64, 128, 256, 512, ..., 559872, 746496, 823543, 839808, 1000000]
For k=7  there are 46 k-powerful numbers <= 10^k: [1, 128, 256, 512, 1024, ..., 7558272, 8388608, 8957952, 9765625, 10000000]
For k=8  there are 52 k-powerful numbers <= 10^k: [1, 256, 512, 1024, 2048, ..., 60466176, 67108864, 80621568, 90699264, 100000000]
For k=9  there are 59 k-powerful numbers <= 10^k: [1, 512, 1024, 2048, 4096, ..., 644972544, 725594112, 816293376, 967458816, 1000000000]
For k=10 there are 68 k-powerful numbers <= 10^k: [1, 1024, 2048, 4096, 8192, ..., 7739670528, 8589934592, 8707129344, 9795520512, 10000000000]
```


### Counting

```ruby
func powerful_count(n, k=2) {
 
    var count = 0
 
    func (m,r) {
        if (r <= k) {
            count += iroot(idiv(n,m), r)
            return nil
        }
        for a in (1 .. iroot(idiv(n,m), r)) {
            a.is_coprime(m) || next
            a.is_squarefree || next
            __FUNC__(m * a**r, r-1)
        }
    }(1, 2*k - 1)
 
    return count
}
 
for k in (2..10) {
    var a = (k+10).of {|j| powerful_count(10**j, k) }
    printf("Number of %2d-powerful numbers <= 10^j, for 0 <= j < #{k+10}: %s\n", k, a)
}
```

#### Output:
```
Number of  2-powerful numbers <= 10^j, for 0 <= j < 12: [1, 4, 14, 54, 185, 619, 2027, 6553, 21044, 67231, 214122, 680330]
Number of  3-powerful numbers <= 10^j, for 0 <= j < 13: [1, 2, 7, 20, 51, 129, 307, 713, 1645, 3721, 8348, 18589, 41136]
Number of  4-powerful numbers <= 10^j, for 0 <= j < 14: [1, 1, 5, 11, 25, 57, 117, 235, 464, 906, 1741, 3312, 6236, 11654]
Number of  5-powerful numbers <= 10^j, for 0 <= j < 15: [1, 1, 3, 8, 16, 32, 63, 117, 211, 375, 659, 1153, 2000, 3402, 5770]
Number of  6-powerful numbers <= 10^j, for 0 <= j < 16: [1, 1, 2, 6, 12, 21, 38, 70, 121, 206, 335, 551, 900, 1451, 2326, 3706]
Number of  7-powerful numbers <= 10^j, for 0 <= j < 17: [1, 1, 1, 4, 10, 16, 26, 46, 77, 129, 204, 318, 495, 761, 1172, 1799, 2740]
Number of  8-powerful numbers <= 10^j, for 0 <= j < 18: [1, 1, 1, 3, 8, 13, 19, 32, 52, 85, 135, 211, 315, 467, 689, 1016, 1496, 2191]
Number of  9-powerful numbers <= 10^j, for 0 <= j < 19: [1, 1, 1, 2, 6, 11, 16, 24, 38, 59, 94, 145, 217, 317, 453, 644, 919, 1308, 1868]
Number of 10-powerful numbers <= 10^j, for 0 <= j < 20: [1, 1, 1, 1, 5, 9, 14, 21, 28, 43, 68, 104, 155, 227, 322, 447, 621, 858, 1192, 1651]
```
