[1]: https://rosettacode.org/wiki/Move-to-front_algorithm

# [Move-to-front algorithm][1]

Implemented using regular expressions:

```ruby
func encode(str) {
    var table = ('a'..'z' -> join)
    str.chars.map { |c|
        var s = ''
        table.sub!(Regex('(.*?)' + c), {|s1| s=s1; c + s1})
        s.len
    }
}
 
func decode(nums) {
    var table = ('a'..'z' -> join)
    nums.map { |n|
        var s = ''
        table.sub!(Regex('(.{' + n + '})(.)'), {|s1, s2| s=s2; s2 + s1})
        s
    }.join
}
 
%w(broood bananaaa hiphophiphop).each { |test|
    var encoded = encode(test)
    say "#{test}: #{encoded}"
    var decoded = decode(encoded)
    print "in" if (decoded != test)
    say "correctly decoded to #{decoded}"
}
```


Alternatively, implemented as a module, using arrays:

```ruby
module MoveToFront {
 
  define ABC = @("a".."z")
 
  func m2f(ar,i) {
    [ar.delete_index(i)] + ar
  }
 
  func encode(str) {
    var ar = ABC+[]
    gather {
      str.each_char { |char|
        take(var i = ar.index(char))
        ar = m2f(ar, i)
      }
    }
  }
 
  func decode(indices) {
    var ar = ABC+[]
    gather {
      indices.each { |i|
        take ar[i]
        ar = m2f(ar, i)
      }
    }.join
  }
}
 
%w(broood bananaaa hiphophiphop).each { |test|
    var encoded = MoveToFront::encode(test)
    say "#{test}: #{encoded}"
    var decoded = MoveToFront::decode(encoded)
    print "in" if (decoded != test)
    say "correctly decoded to #{decoded}"
}
```

#### Output:
```
broood: 1 17 15 0 0 5
correctly decoded to broood
bananaaa: 1 1 13 1 1 1 0 0
correctly decoded to bananaaa
hiphophiphop: 7 8 15 2 15 2 2 3 2 2 3 2
correctly decoded to hiphophiphop
```
