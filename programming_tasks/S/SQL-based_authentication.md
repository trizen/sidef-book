[1]: https://rosettacode.org/wiki/SQL-based_authentication

# [SQL-based authentication][1]

```ruby
require('DBI')
 
 # returns a database handle configured to throw an exception on query errors
func connect_db(dbname, host, user, pass) {
    var db = %O<DBI>.connect("dbi:mysql:#{dbname}:#{host}", user, pass)
    db || die (global DBI::errstr)
    db{:RaiseError} = 1
    db
}
 
 # if the user was successfully created, returns its user id.
 # if the name was already in use, returns nil.
func create_user(db, user, pass) {
    var salt = "C*".pack(16.of { 256.irand }...)
    db.do(
        "INSERT IGNORE INTO users (username, pass_salt, pass_md5)
         VALUES (?, ?, unhex(md5(concat(pass_salt, ?))))", nil, user, salt, pass
    ) ? db{:mysql_insertid} : nil
}
 
 # if the user is authentic, returns its user id.  otherwise returns nil.
func authenticate_user(db, user, pass) {
    db.selectrow_array("SELECT userid FROM users WHERE
        username=? AND pass_md5=unhex(md5(concat(pass_salt, ?)))",
        nil, user, pass
    )
}
```
