[1]: http://rosettacode.org/wiki/Random_number_generator_(included)

# [Random number generator (included)][1]

Latest versions of Sidef use the Mersenne Twister algorithm to compute pseudorandom numbers, with different initial seeds (and implementations) for floating-points and integers.

```ruby
say 1.rand          # random float in the interval [0,1)
say 100.irand       # random integer in the interval [0,100)
```