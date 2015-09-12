[1]: http://rosettacode.org/wiki/Web_scraping

# [Web scraping][1]

```ruby
var ua = frequire('LWP::Simple');
var url = 'http://tycho.usno.navy.mil/cgi-bin/timer.pl';
ua.get(url) ~~ /<BR>(.+? UTC)/ && say $1;
```