[1]: https://rosettacode.org/wiki/HTTPS/Authenticated

# [HTTPS/Authenticated][1]

```ruby
require('WWW::Mechanize')

var mech = %O<WWW::Mechanize>.new(
    cookie_jar => Hash(),
    agent => 'Mozilla/5.0',
    show_progress => 1,
)

mech.get('https://login.yahoo.com/')
mech.submit_form(
    form_id => 'mbr-login-form',   # form id
    fields => Hash(
        'login'  => 'XXXXXX',
        'passwd' => 'YYYYYY',
))
```
