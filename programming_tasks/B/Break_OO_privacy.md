[1]: https://rosettacode.org/wiki/Break_OO_privacy

# [Break OO privacy][1]

Sidef's object model does not enforce privacy, but it allows storing private attributes inside the container of an object, which is an hash:

```ruby
class Example {
    has public = "foo"
    method init {
        self{:private} = "secret"
    }
}
 
var obj = Example();
 
# Access public attributes
say obj.public;                 #=> "foo"
say obj{:public};               #=> "foo"
 
# Access private attributes
say obj{:private};              #=> "secret"
```