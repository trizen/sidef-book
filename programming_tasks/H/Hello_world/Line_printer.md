[1]: https://rosettacode.org/wiki/Hello_world/Line_printer

# [Hello world/Line printer][1]

```ruby
Sys.open(\var fh, '>', '/dev/lp0') \
    && fh.say("Hello World!")      \
    && fh.close
```
