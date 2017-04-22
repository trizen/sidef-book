[1]: http://rosettacode.org/wiki/Singleton

# [Singleton][1]

```ruby
class Singleton(name) {
    static instance
 
    method new(name) {
        instance := Singleton.bless(Hash(:name => name))
    }
    method new {
        Singleton.new(nil)
    }
}
 
var s1 = Singleton('foo')
say s1.name                 #=> 'foo'
say s1.object_id            #=> '30424504'
 
var s2 = Singleton()
say s2.name                 #=> 'foo'
say s2.object_id            #=> '30424504'
 
s2.name = 'bar'             # change name in s2
say s1.name                 #=> 'bar'
```
