[1]: https://rosettacode.org/wiki/Practical_numbers

# [Practical numbers][1]

Built-in:

```ruby
say is_practical(2**128 + 1)   #=> false
say is_practical(2**128 + 4)   #=> true
```


Slow implementation (as the task requires):

```ruby
func is_practical(n) {
 
    var set = Set()
 
    n.divisors.grep { _ < n }.subsets {|*a|
        set << a.sum
    }
 
    1..n-1 -> all { set.has(_) }
}
 
var from = 1
var upto = 333
 
var list = (from..upto).grep { is_practical(_) }
 
say "There are #{list.len} practical numbers in the range #{from}..#{upto}."
say "#{list.first(10).join(', ')} ... #{list.last(10).join(', ')}\n"
 
for n in ([666, 6666, 66666]) {
    say "#{'%5s' % n } is practical? #{is_practical(n)}"
}
```


Efficient algorithm:

```ruby
func is_practical(n) {
 
    n.is_odd && return (n == 1)
    n.is_pos || return false
 
    var p = 1
    var f = n.factor_exp
 
    f.each_cons(2, {|a,b|
        p *= sigma(a.head**a.tail)
        b.head > (1 + p) && return false
    })
 
    return true
}
```

#### Output:
```
There are 77 practical numbers in the range 1..333.
1, 2, 4, 6, 8, 12, 16, 18, 20, 24 ... 288, 294, 300, 304, 306, 308, 312, 320, 324, 330

  666 is practical? true
 6666 is practical? true
66666 is practical? false
```
