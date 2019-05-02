[1]: https://rosettacode.org/wiki/Spelling_of_ordinal_numbers

# [Spelling of ordinal numbers][1]

```ruby
var lingua_en = frequire('Lingua::EN::Numbers')
var tests = [1,2,3,4,5,11,65,100,101,272,23456,8007006005004003]
 
tests.each {|n|
    printf("%16s : %s\n", n, lingua_en.num2en_ordinal(n))
}
```

#### Output:
```
               1 : first
               2 : second
               3 : third
               4 : fourth
               5 : fifth
              11 : eleventh
              65 : sixty-fifth
             100 : one hundredth
             101 : one hundred and first
             272 : two hundred and seventy-second
           23456 : twenty-three thousand four hundred and fifty-sixth
8007006005004003 : eight quadrillion, seven trillion, six billion, five million, four thousand and third
```
