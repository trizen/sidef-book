[1]: http://rosettacode.org/wiki/FTP

# [FTP][1]

```ruby
require 'Net::FTP';
 
var ftp = %s'Net::FTP'.new('ftp.ed.ac.uk', Passive => 1);
ftp.login('anonymous','aaa@gmail.com');
ftp.cwd('pub/courses');
[ftp.dir].each {|line| say line };
ftp.binary;   # set binary mode
ftp.get("make.notes.tar");
ftp.quit;
```
