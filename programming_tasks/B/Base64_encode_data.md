[1]: http://rosettacode.org/wiki/Base64_encode_data

# [Base64 encode data][1]

```ruby
var base64 = frequire('MIME::Base64');
 
var file = %f'favicon.ico';
file.open('<:raw', \var fh, \var err) || die err;
 
print base64.encode_base64(fh.slurp);
```