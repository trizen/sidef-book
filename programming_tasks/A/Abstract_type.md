[1]: https://rosettacode.org/wiki/Abstract_type

# [Abstract type][1]

```ruby
class A {
    # must be filled in by the class which will inherit it
    method abstract() { die 'Unimplemented' };
 
    # can be overridden in the class, but that's not mandatory
    method concrete() { say '# 42' };
}
 
class SomeClass << A {
    method abstract() {
        say "# made concrete in class"
    }
}
 
var obj = SomeClass.new;
obj.abstract();   # made concrete in class
obj.concrete();   # 42
```