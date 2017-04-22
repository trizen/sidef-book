[1]: http://rosettacode.org/wiki/General_FizzBuzz

# [General FizzBuzz][1]

```ruby
class FizzBuzz(schema=Hash(<3 Fizz 5 Buzz>...)) {
    method filter(this) {
        var fb = ''
        schema.sort_by {|k,_| k.to_i }.each { |pair|
            fb += (pair[0].to_i `divides` this ? pair[1] : '')
        }
        fb.len > 0 ? fb : this
    }
}
 
func GeneralFizzBuzz(upto, schema) {
    var ping = FizzBuzz()
    if (nil != schema) {
        ping.schema = schema.to_hash
    }
    (1..upto).map {|i| ping.filter(i) }
}
 
GeneralFizzBuzz(20, <3 Fizz 5 Buzz 7 Baxx>).each { .say }
```

#### Output:
```
1
2
Fizz
4
Buzz
Fizz
Baxx
8
Fizz
Buzz
11
Fizz
13
Baxx
FizzBuzz
16
17
Fizz
19
Buzz
```
