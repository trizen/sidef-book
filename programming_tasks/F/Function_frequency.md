[1]: http://rosettacode.org/wiki/Function_frequency

# [Function frequency][1]

Sidef provides full access to its parser, allowing us to inspect all the declarations within a program.

```ruby
func foo { }
func bar { }

foo(); foo(); foo()
bar(); bar();

var data = Perl.to_sidef(Parser{:vars}{:main}).flatten

data.sort_by { |v| -v{:count} }.first(10).each { |entry|
    if (entry{:type} == :func) {
        say ("Function `#{entry{:name}}` (declared at line",
             " #{entry{:line}}) is used #{entry{:count}} times")
    }
}
```

#### Output:
```
Function `foo` (declared at line 1) is used 3 times
Function `bar` (declared at line 2) is used 2 times
```
