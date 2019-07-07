[1]: https://rosettacode.org/wiki/Bell_numbers

# [Bell numbers][1]

Built-in:

```ruby
say 15.of { .bell }
```


Formula as a sum of Stirling numbers of the second kind:

```ruby
func bell(n) { sum(0..n, {|k| stirling2(n, k) }) }
```


Via Aitken's array (optimized for space):

```ruby
func bell_numbers (n) {
 
    var acc = []
    var bell = [1]
 
    (n-1).times {
        acc.unshift(bell[-1])
        acc.accumulate!
        bell.push(acc[-1])
    }
 
    bell
}
 
var B = bell_numbers(50)
say "The first 15 Bell numbers: #{B.first(15).join(', ')}"
say "The fiftieth Bell number : #{B[50-1]}"
```

#### Output:
```
The first 15 Bell numbers: 1, 1, 2, 5, 15, 52, 203, 877, 4140, 21147, 115975, 678570, 4213597, 27644437, 190899322
The fiftieth Bell number : 10726137154573358400342215518590002633917247281
```


Aitken's array:

```ruby
func aitken_array (n) {
 
    var A = [1]
 
    [[1]] + (n-1).of {
        A = [A[-1], A...].accumulate
    }
}
 
aitken_array(10).each { .say }
```

#### Output:
```
[1]
[1, 2]
[2, 3, 5]
[5, 7, 10, 15]
[15, 20, 27, 37, 52]
[52, 67, 87, 114, 151, 203]
[203, 255, 322, 409, 523, 674, 877]
[877, 1080, 1335, 1657, 2066, 2589, 3263, 4140]
[4140, 5017, 6097, 7432, 9089, 11155, 13744, 17007, 21147]
[21147, 25287, 30304, 36401, 43833, 52922, 64077, 77821, 94828, 115975]
```


Aitken's array (recursive definition):

```ruby
func A((0), (0))       { 1 }
func A(n, (0))         { A(n-1, n-1) }
func A(n, k) is cached { A(n, k-1) + A(n-1, k-1) }
 
for n in (^10) {
    say (0..n -> map{|k| A(n, k) })
}
```


(same output as above)
