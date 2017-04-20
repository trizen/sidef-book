[1]: http://rosettacode.org/wiki/Balanced_brackets

# [Balanced brackets][1]

```ruby
func balanced (str) {
 
    var depth = 0
    str.each { |c|
           if(c=='['){ ++depth }
        elsif(c==']'){ --depth < 0 && return false }
    }
 
    return !depth
}

for str [']','[','[[]','][]','[[]]','[[]]]][][]]','x[ y [ [] z ]][ 1 ][]abcd'] {
    printf("%sbalanced\t: %s\n", balanced(str) ? "" : "NOT ", str)
}
```

#### Output:
```
NOT balanced    : ]
NOT balanced    : [
NOT balanced    : [[]
NOT balanced    : ][]
balanced        : [[]]
NOT balanced    : [[]]]][][]]
balanced        : x[ y [ [] z ]][ 1 ][]abcd
```
