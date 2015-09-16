[1]: http://rosettacode.org/wiki/Loop_over_multiple_arrays_simultaneously

# [Loop over multiple arrays simultaneously][1]

The simplest way is to use _MultiArray_s:

```ruby
MultiArray.new(%w(a b c),%w(A B C),%w(1 2 3)).each { |i,j,k|
    say "#{i}#{j}#{k}";
};
```
