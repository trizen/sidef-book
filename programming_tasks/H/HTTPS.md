[1]: https://rosettacode.org/wiki/HTTPS

# [HTTPS][1]

```ruby
require('LWP::UserAgent')
require('LWP::Protocol::https')

func get(url) {
    static ua = %O<LWP::UserAgent>.new(
        agent => 'Mozilla/5.0',
        ssl_opts => Hash(verify_hostname => 1),
    )
    var resp = ua.get(url)
    if (resp.is_success) {
        return resp.decoded_content
    }
    die "Failed to GET #{url}: #{resp.status_line}"
}

say get("https://rosettacode.org")
```
