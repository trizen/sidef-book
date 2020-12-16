[1]: http://rosettacode.org/wiki/Exceptions/Catch_an_exception_thrown_in_a_nested_call

# [Exceptions/Catch an exception thrown in a nested call][1]

```ruby
func baz(i) { die "U#{i}" }
func bar(i) { baz(i)      }
 
func foo {
    [0, 1].each { |i|
        try   { bar(i) }
        catch { |msg|
            msg ~~ /^U0/ ? say "Function foo() caught exception U0"
                         : die msg       # re-raise the exception
        }
    }
}
 
foo()
```

#### Output:
```
Function foo() caught exception U0
U1 at test.sf line 1. at test.sf line 9.
```
