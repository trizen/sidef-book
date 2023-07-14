[1]: https://rosettacode.org/wiki/Anagrams

# [Anagrams][1]

```ruby
func main(file) {
    file.open_r(\var fh, \var err) ->
        || die "Can't open file `#{file}' for reading: #{err}\n";
 
    var vls = fh.words.group_by{.sort}.values;
    var max = vls.map{.len}.max;
    vls.grep{.len == max}.each{.join("\t").say};
}
 
main(%f'/tmp/unixdict.txt');
```

#### Output:
```
alger   glare   lager   large   regal
abel    able    bale    bela    elba
angel   angle   galen   glean   lange
elan    lane    lean    lena    neal
evil    levi    live    veil    vile
caret   carte   cater   crate   trace
```
