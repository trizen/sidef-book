[1]: http://rosettacode.org/wiki/Compare_a_list_of_strings

# [Compare a list of strings][1]

Short-circuiting:

```ruby
1..arr.offset -> all{ arr[0] == arr[_] };  # All equal
1..arr.offset -> all{ arr[_-1] < arr[_] }; # Strictly ascending
```


Non short-circuiting:

```ruby
arr.unique.len == 1;    # all equal?
arr == arr.sort;        # sorted?
```