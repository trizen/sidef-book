[1]: https://rosettacode.org/wiki/Variadic_function

# [Variadic function][1]

A parameter declared with "\*", can take any number of arguments of any type.

```ruby
func print_all(*things) {
    things.each { |x| say x }
}
```


This function can be called with any number of arguments:

```ruby
print_all(4, 3, 5, 6, 4, 3)
print_all(4, 3, 5)
print_all("Rosetta", "Code", "Is", "Awesome!")
```


Also, there is "..." which transforms an array into a list of arguments.

```ruby
var args = ["Rosetta", "Code", "Is", "Awesome!"]
print_all(args...)
```
