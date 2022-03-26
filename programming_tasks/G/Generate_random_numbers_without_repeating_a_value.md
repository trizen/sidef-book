[1]: https://rosettacode.org/wiki/Generate_random_numbers_without_repeating_a_value

# [Generate random numbers without repeating a value][1]

```ruby
var nums = (1..20).to_a
5.times{ say nums.shuffle.join(" ") }
```

#### Output:
```
7 16 11 2 8 5 19 1 3 17 10 4 18 6 9 13 15 20 12 14
20 4 18 7 16 2 3 10 5 13 19 17 12 1 6 11 8 15 14 9
2 6 8 18 5 15 1 13 19 17 12 3 4 7 20 16 10 11 9 14
2 18 10 16 12 14 7 13 1 8 15 20 6 17 3 11 5 9 4 19
2 17 14 15 5 13 4 16 11 18 1 10 9 7 6 12 20 3 8 19
```
