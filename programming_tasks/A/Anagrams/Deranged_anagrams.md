[1]: https://rosettacode.org/wiki/Anagrams/Deranged_anagrams

# [Anagrams/Deranged anagrams][1]

```ruby
func find_deranged(Array a) {
    for i in (^a) {
        for j in (i+1 .. a.end) {
            overlaps(a[i], a[j]) || (
                printf("length %d: %s => %s\n", a[i].len, a[i], a[j])
                return true
            )
        }
    }
    return false
}

func main(File file) {

    file.open_r(\var fh, \var err) ->
        || die "Can't open file `#{file}' for reading: #{err}\n"

    var letter_list = Hash()

    # Store anagrams in hash table by letters they contain
    fh.words.each { |word|
        letter_list{word.sort} := [] << word
    }

    letter_list.keys                        \
         .grep {|k| letter_list{k}.len > 1} \     # take only ones with anagrams
         .sort {|a,b| b.len <=> a.len}      \     # sort by length, descending
         .each {|key|

        # If we find a pair, they are the longested due to the sort before
        find_deranged(letter_list{key}) && break
    }
}

main(%f'/tmp/unixdict.txt')
```

#### Output:
```
length 10: excitation => intoxicate
```
