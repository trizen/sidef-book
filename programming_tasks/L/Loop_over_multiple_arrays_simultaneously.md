[1]: http://rosettacode.org/wiki/Loop_over_multiple_arrays_simultaneously

# [Loop over multiple arrays simultaneously][1]

The simplest way is to use _MultiArray_s:

```ruby
MultiArray.new(%w(a b c),%w(A B C),%w(1 2 3)).each { |i,j,k|
    say "#{i}#{j}#{k}";
};
```


Another approach is to zip two arrays at a time and reduce pairs of their elements into one element.

```ruby
func multi_zip(zipped) {
    .each { |arr|
        zipped.zip!(arr).reducePairs!{.flatten};
    };
    return zipped;
}
 
multi_zip(%w(a b c),%w(A B C),%w(1 2 3)).each{ |i,j,k|
    say "#{i}#{j}#{k}";
};
```


The returned array will have the same number of elements as the shortest array.