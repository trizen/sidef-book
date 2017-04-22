[1]: http://rosettacode.org/wiki/Terminal_control/Unicode_output

# [Terminal control/Unicode output][1]

```ruby
if (/\bUTF-?8/i ~~ [ENV{"LC_ALL","LC_CTYPE","LANG"}]) {
    say "△"
} else {
    die "Terminal can't handle UTF-8.\n"
}
```
