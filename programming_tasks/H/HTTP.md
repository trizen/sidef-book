[1]: https://rosettacode.org/wiki/HTTP

# [HTTP][1]

Sidef can load and use Perl modules:

```ruby
func get(url) {
    var lwp = (
        try   { require('LWP::UserAgent') }
        catch { warn "'LWP::UserAgent' is not installed!"; return nil }
    )
    var ua = lwp.new(agent => 'Mozilla/5.0')
    if (var resp = ua.get(url); resp.is_success) {
        return resp.decoded_content
    }
    return nil
}
 
print get("https://rosettacode.org")
```
