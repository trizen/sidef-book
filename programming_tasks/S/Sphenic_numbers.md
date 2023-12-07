[1]: https://rosettacode.org/wiki/Sphenic_numbers

# [Sphenic numbers][1]

```ruby
func sphenic_numbers(upto) {
    3.squarefree_almost_primes(upto)
}

func sphenic_triplets(upto) {
    var S = sphenic_numbers(upto)
    S.grep_kv {|k,v| v+2 == S[k+2] }.map{ [_, _+1, _+2] }
}

with (1e3) {|n|
    say "Sphenic numbers less than #{n.commify}:"
    sphenic_numbers(n-1).slices(15).each{.map{'%4s' % _}.join.say}
}

with (1e4) {|n|
    say "\nSphenic triplets less than #{n.commify}:"
    sphenic_triplets(n-1).each{.say}
}

with (1e6) {|n|
    var triplets = sphenic_triplets(n-1)
    say "\nThere are #{3.squarefree_almost_prime_count(n-1)} sphenic numbers less than #{n.commify}."
    say "There are #{triplets.len} sphenic triplets less than #{n.commify}."
    with (2e5) {|n| say "The #{n.commify}th sphenic number is: #{nth_squarefree_almost_prime(n, 3)}." }
    with (5e3) {|n| say "The #{n.commify}th sphenic triplet is: #{triplets[n-1]}." }
}
```

#### Output:
```
Sphenic numbers less than 1,000:
  30  42  66  70  78 102 105 110 114 130 138 154 165 170 174
 182 186 190 195 222 230 231 238 246 255 258 266 273 282 285
 286 290 310 318 322 345 354 357 366 370 374 385 399 402 406
 410 418 426 429 430 434 435 438 442 455 465 470 474 483 494
 498 506 518 530 534 555 561 574 582 590 595 598 602 606 609
 610 615 618 627 638 642 645 646 651 654 658 663 665 670 678
 682 705 710 715 730 741 742 754 759 762 777 782 786 790 795
 805 806 814 822 826 830 834 854 861 874 885 890 894 897 902
 903 906 915 935 938 942 946 957 962 969 970 978 986 987 994

Sphenic triplets less than 10,000:
[1309, 1310, 1311]
[1885, 1886, 1887]
[2013, 2014, 2015]
[2665, 2666, 2667]
[3729, 3730, 3731]
[5133, 5134, 5135]
[6061, 6062, 6063]
[6213, 6214, 6215]
[6305, 6306, 6307]
[6477, 6478, 6479]
[6853, 6854, 6855]
[6985, 6986, 6987]
[7257, 7258, 7259]
[7953, 7954, 7955]
[8393, 8394, 8395]
[8533, 8534, 8535]
[8785, 8786, 8787]
[9213, 9214, 9215]
[9453, 9454, 9455]
[9821, 9822, 9823]
[9877, 9878, 9879]

There are 206964 sphenic numbers less than 1,000,000.
There are 5457 sphenic triplets less than 1,000,000.
The 200,000th sphenic number is: 966467.
The 5,000th sphenic triplet is: [918005, 918006, 918007].
```
