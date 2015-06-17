[1]: http://rosettacode.org/wiki/Terminal_control/Unicode_output

# [Terminal control/Unicode output][1]

```ruby
if (ENV["LC_ALL","LC_CTYPE","LANG"].any{_ ~~ /\bUTF-?8/i}) {
    say "△"
} else {
    die "Terminal can't handle UTF-8.";
}
```