[1]: https://rosettacode.org/wiki/Random_number_generator_(device)

# [Random number generator (device)][1]

```ruby
func urandom() {
    static device = %f'/dev/urandom'

    device.open('<:raw', \var fh, \var err) ->
        || die "Can't open `#{device}': #{err}"

    fh.sysread(\var noise, 4)
    'L'.unpack(noise)
}

say urandom()    # sample: 1989353410
```
