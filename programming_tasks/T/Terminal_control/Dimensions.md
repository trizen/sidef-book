[1]: http://rosettacode.org/wiki/Terminal_control/Dimensions

# [Terminal control/Dimensions][1]

```ruby
var stty = `stty -a`
var lines = stty.match(/\brows\h+(\d+)/)
var cols  = stty.match(/\bcolumns\h+(\d+)/)
say "#{lines} #{cols}"
```

#### Output:
```
24 80
```
