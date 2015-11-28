[1]: http://rosettacode.org/wiki/CSV_data_manipulation

# [CSV data manipulation][1]

For simple files we can use the _split_ method.

```ruby
# Read
var csvfile = %f'data.csv';
var fh = csvfile.open_r;
var header = fh.line.trim_end.split(',');
var csv = fh.lines.map { .trim_end.split(',').map{.to_num} };
fh.close;
 
# Write
var out = csvfile.open_w;
out.say([header..., 'SUM'].join(','));
csv.each { |row| out.say([row..., row.sum].join(',')) };
out.close;
```


For complex files, the _Text::CSV_ library is recommended.

```ruby
var csv = require('Text::CSV').new(
    Hash(eol => "\n")
);
 
# Open
var csvfile = %f'data.csv';
var fh = csvfile.open_r;
 
# Read
var rows = [];
var header = csv.getline(fh);
while (var row = csv.getline(fh)) {
    rows.append(row.map{.to_num});
}
 
# Process
header.append('SUM');
rows.each { |row| row.append(row.sum) };
 
# Write
var out = csvfile.open_w;
[header, rows...].each { |row|
    csv.print(out, row);
};
```
