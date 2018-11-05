# Block

A Block is a special object which encapsulates zero or more statements which can be executed at a later time. The block itself can be stored inside variables, arrays or passed as argument to functions.

```ruby
{
    say "Hello world!"
}
```

The `run` method on `Block` objects is used to call the block with arguments.

```ruby
{
    say "Hello #{_}!"
}.run("you")           # prints "Hello you!"

```
