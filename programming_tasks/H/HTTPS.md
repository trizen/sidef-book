[1]: http://rosettacode.org/wiki/HTTPS

# [HTTPS][1]

```ruby
var lwp = require('LWP::UserAgent')    # LWP::Protocol::https is needed
var url = 'https://rosettacode.org'
 
var ua = lwp.new(
    agent    => 'Mozilla/5.0',
    ssl_opts => Hash(verify_hostname => 1),
)
 
var resp = ua.get(url)
resp.is_success || die "Failed to GET #{url}: #{resp.status_line}"
print resp.decoded_content
```
