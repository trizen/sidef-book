[1]: http://rosettacode.org/wiki/Web_scraping

# [Web scraping][1]

```ruby
var ua = frequire('LWP::Simple');
var url = 'http://tycho.usno.navy.mil/cgi-bin/timer.pl';
var match = /<BR>(.+? UTC)/.match(ua.get(url));
say match[0] if match;
```

#### Output:
```
Oct. 27, 00:20:50 UTC
```