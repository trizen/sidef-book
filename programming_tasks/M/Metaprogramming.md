[1]: http://rosettacode.org/wiki/Metaprogramming

# [Metaprogramming][1]

Sidef recognizes all mathematical operators in Unicode and allows the user to define methods that behave like infix operators, even for built-in types.

```ruby
class Number {
    method ⊕(arg) {
        self + arg
    }
}
 
say (21 ⊕ 42)
```


Another example of metaprogramming, is the definition of methods at run-time:

```ruby
var colors = Hash(
               'black'   => "000",
               'red'     => "f00",
               'green'   => "0f0",
               'yellow'  => "ff0",
               'blue'    => "00f",
               'magenta' => "f0f",
               'cyan'    => "0ff",
               'white'   => "fff",
             )
 
colors.each { |color, code|
    String.def_method("in_#{color}", func (self) {
        '<span style="color: #' + code + '">' + self + '</span>'
    })
}
 
say "blue".in_blue;
say "red".in_red;
say "white".in_white;
```

#### Output:
```
<span style="color: #00f">blue</span>
<span style="color: #f00">red</span>
<span style="color: #fff">white</span>
```