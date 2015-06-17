[1]: http://rosettacode.org/wiki/Enumerations

# [Enumerations][1]

Implicit:

```ruby
enum {Apple, Banana, Cherry};   # numbered 0 through 2
```


Explicit:

```ruby
enum {
    Apple=3,
    Banana,         # gets the value 4
    Cherry="a",
    Orange,         # gets the value "b"
};
```