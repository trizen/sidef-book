[1]: http://rosettacode.org/wiki/MD5

# [MD5][1]

```ruby
var digest = frequire('Digest::MD5');
say digest.md5_hex("The quick brown fox jumped over the lazy dog's back");
```


The same in OO manner

```ruby
var md5 = require('Digest::MD5').new;
md5.add("The quick brown fox jumped over the lazy dog's back");
say md5.hexdigest;
```