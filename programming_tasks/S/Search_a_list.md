[1]: https://rosettacode.org/wiki/Search_a_list

# [Search a list][1]

```ruby
var haystack = %w(Zig Zag Wally Ronald Bush Krusty Charlie Bush Bozo)
 
%w(Bush Washington).each { |needle|
    var i = haystack.first_index{|item| item == needle}
    if (i >= 0) {
        say "#{i} #{needle}"
    } else {
        die "#{needle} is not in haystack"
    }
}
```

#### Output:
```
4 Bush
Washington is not in haystack at find.sf line 9.
```


Extra credit:

```ruby
var haystack = %w(Zig Zag Wally Ronald Bush Krusty Charlie Bush Bozo)
say haystack.last_index{|item| item == "Bush"}
```

#### Output:
```
7
```
