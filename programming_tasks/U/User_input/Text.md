[1]: http://rosettacode.org/wiki/User_input/Text

# [User input/Text][1]

Using the *read(Type)* built-in function:

```ruby
var s = read(String)
var i = read(Number)     # auto-conversion to a number
```


or using the *Sys.readln(msg)* method:

```ruby
var s = Sys.readln("Enter a string: ")
var i = Sys.readln("Enter a number: ").to_i
```
