[1]: https://rosettacode.org/wiki/Append_a_record_to_the_end_of_a_text_file

# [Append a record to the end of a text file][1]

```ruby
define (
    RECORD_FIELDS = %w(account password UID GID GECOS directory shell),
    GECOS_FIELDS  = %w(fullname office extension homephone email),
    RECORD_SEP    = ':',
    GECOS_SEP     = ',',
    PASSWD_FILE   = 'passwd.txt',
)
 
# here's our three records
var records_to_write = [
    Hash(
        account  => 'jsmith',
        password => 'x',
        UID      => 1001,
        GID      => 1000,
        GECOS    => Hash(
            fullname  => 'John Smith',
            office    => 'Room 1007',
            extension => '(234)555-8917',
            homephone => '(234)555-0077',
            email     => 'jsmith@rosettacode.org',
        ),
        directory => '/home/jsmith',
        shell     => '/bin/bash',
    ),
    Hash(
        account  => 'jdoe',
        password => 'x',
        UID      => 1002,
        GID      => 1000,
        GECOS    => Hash(
            fullname  => 'Jane Doe',
            office    => 'Room 1004',
            extension => '(234)555-8914',
            homephone => '(234)555-0044',
            email     => 'jdoe@rosettacode.org',
        ),
        directory => '/home/jdoe',
        shell     => '/bin/bash',
    ),
];
 
var record_to_append = Hash(
    account  => 'xyz',
    password => 'x',
    UID      => 1003,
    GID      => 1000,
    GECOS    => Hash(
        fullname  => 'X Yz',
        office    => 'Room 1003',
        extension => '(234)555-8913',
        homephone => '(234)555-0033',
        email     => 'xyz@rosettacode.org',
    ),
    directory => '/home/xyz',
    shell     => '/bin/bash',
);
 
func record_to_string(rec, sep = RECORD_SEP, fields = RECORD_FIELDS) {
    gather {
        fields.each { |field|
            var r = rec{field} \\ die "Field #{field} not found"
            take(field == 'GECOS' ? record_to_string(r, GECOS_SEP, GECOS_FIELDS)
                                  : r)
        }
    }.join(sep)
}
 
func write_records_to_file(records, filename = PASSWD_FILE, append = false) {
    File(filename).(append ? :open_a : :open_w)(\var fh, \var err)
    err && die "Can't open #{filename}: #{err}";
    fh.flock(File.LOCK_EX) || die "Can't lock #{filename}: $!"
    fh.seek(0, File.SEEK_END) || die "Can't seek #{filename}: $!"
    records.each { |record| fh.say(record_to_string(record)) }
    fh.flock(File.LOCK_UN) || die "Can't unlock #{filename}: $!"
    fh.close
}
 
# write two records to file
write_records_to_file(records: records_to_write);
 
# append one more record to file
write_records_to_file(records: [record_to_append], append: true);
 
# test
File(PASSWD_FILE).open_r(\var fh, \var err)
err && die "Can't open file #{PASSWD_FILE}: #{err}"
var lines = fh.lines
 
# There should be more than one line
assert(lines.len > 1)
 
# Check the last line
assert_eq(lines[-1], 'xyz:x:1003:1000:X Yz,Room 1003,(234)555-8913,' +
                     '(234)555-0033,xyz@rosettacode.org:/home/xyz:/bin/bash')
 
say "** Test passed!"
```


Note that flock uses advisory lock; some other program (if it doesn't use flock) can still unexpectedly write to the file.
