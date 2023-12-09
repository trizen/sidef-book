[1]: https://rosettacode.org/wiki/HTTP

# [HTTP][1]

Sidef can load and use Perl modules:

```ruby
require('HTTP::Tiny')

func get(url) {
    static ua = %O<HTTP::Tiny>.new(agent => 'Mozilla/5.0')
    var resp = ua.get(url)
    if (resp{:success}) {
        return resp{:content}.decode_utf8
    }
    return nil
}

say get("http://rosettacode.org")
```
