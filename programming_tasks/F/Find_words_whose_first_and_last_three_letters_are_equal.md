[1]: https://rosettacode.org/wiki/Find_words_whose_first_and_last_three_letters_are_equal

# [Find words whose first and last three letters are equal][1]

```ruby
File("unixdict.txt").open_r.each {|word|
    word.len > 5 || next
    if (word.ends_with(word.first(3))) {
        say word
    }
}
```

#### Output:
```
antiperspirant
calendrical
einstein
hotshot
murmur
oshkosh
tartar
testes
```
