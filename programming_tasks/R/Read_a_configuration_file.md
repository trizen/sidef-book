[1]: http://rosettacode.org/wiki/Read_a_configuration_file

# [Read a configuration file][1]

```ruby
var fullname = (var favouritefruit = "");
var needspeeling = (var seedsremoved = false);
var otherfamily = [];
 
ARGF.each { |line|
    var(key, value) = line.strip.split(/\h+/, 2)...;
 
    given(key) {
        when (nil)              { }
        when (/^([#;]|\h*$)/)   { }
        when ("FULLNAME")       { fullname = value }
        when ("FAVOURITEFRUIT") { favouritefruit = value }
        when ("NEEDSPEELING")   { needspeeling = true }
        when ("SEEDSREMOVED")   { seedsremoved = true }
        when ("OTHERFAMILY")    { otherfamily = value.split(',')»strip»() }
        default                 { say "#{key}: unknown key" }
    }
}
 
say "fullname       = #{fullname}";
say "favouritefruit = #{favouritefruit}";
say "needspeeling   = #{needspeeling}";
say "seedsremoved   = #{seedsremoved}";
 
otherfamily.each_kv {|i, name|
    say "otherfamily(#{i+1}) = #{name}";
}
```

#### Output:
```
fullname       = Foo Barber
favouritefruit = banana
needspeeling   = true
seedsremoved   = false
otherfamily(1) = Rhu Barber
otherfamily(2) = Harry Barber
```
