[1]: http://rosettacode.org/wiki/Stair-climbing_puzzle

# [Stair-climbing puzzle][1]

```ruby
func step_up() {
    while (!step()) {
        step_up()
    }
}
```
