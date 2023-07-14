[1]: https://rosettacode.org/wiki/FTP

# [FTP][1]

```ruby
require('Net::FTP')
 
var ftp = %O<Net::FTP>.new('ftp.ed.ac.uk', Passive => 1)
ftp.login('anonymous','email@example.com')
ftp.cwd('pub/courses')
[ftp.dir].each {|line| say line }
ftp.binary;   # set binary mode
ftp.get("make.notes.tar")
ftp.quit
```
