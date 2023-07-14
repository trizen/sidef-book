[1]: https://rosettacode.org/wiki/Compare_a_list_of_strings

# [Compare a list of strings][1]

Short-circuiting:

```ruby
1..arr.end -> all{ arr[0] == arr[_] }   # all equal
1..arr.end -> all{ arr[_-1] < arr[_] }  # strictly ascending
```


Non short-circuiting:

```ruby
arr.uniq.len == 1      # all equal
arr == arr.uniq.sort   # strictly ascending
```
