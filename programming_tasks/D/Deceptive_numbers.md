[1]: https://rosettacode.org/wiki/Deceptive_numbers

# [Deceptive numbers][1]

```ruby
say 100.by {|n|
    n.is_composite && (divmod(powmod(10, n-1, n)-1, 9, n) == 0)
}.join(' ')
```

#### Output:
```
91 259 451 481 703 1729 2821 2981 3367 4141 4187 5461 6533 6541 6601 7471 7777 8149 8401 8911 10001 11111 12403 13981 14701 14911 15211 15841 19201 21931 22321 24013 24661 27613 29341 34133 34441 35113 38503 41041 45527 46657 48433 50851 50881 52633 54913 57181 63139 63973 65311 66991 67861 68101 75361 79003 82513 83119 94139 95161 97273 97681 100001 101101 101491 102173 108691 113201 115627 115921 118301 118957 122221 126217 128713 130351 131821 134821 134863 137137 137149 138481 139231 145181 147001 148417 152551 158497 162401 164761 166499 170017 172081 179881 188191 188269 188461 188501 196651 201917
```