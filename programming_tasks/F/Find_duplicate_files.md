[1]: https://rosettacode.org/wiki/Find_duplicate_files

# [Find duplicate files][1]

It uses the portable _File::Find_ module which means that it should work, virtually, on any platform.

```ruby
# usage: sidef fdf.sf [size] [dir1] [...]

require('File::Find')

func find_duplicate_files(Block code, size_min=0, *dirs) {
    var files = Hash()
    %S<File::Find>.find(
        Hash(
            no_chdir => true,
            wanted   => func(arg) {
                var file = File(arg)
                file.is_file || return()
                file.is_link && return()
                var size = file.size
                size >= size_min || return()
                files{size} := [] << file
            },
        ) => dirs...
    )

    files.values.each { |set|
        set.len > 1 || next
        var dups = Hash()
        for i in (^set.end) {
            for (var j = set.end; j > i; --j) {
                if (set[i].compare(set[j]) == 0) {
                    dups{set[i]} := [] << set.pop_at(j++)
                }
            }
        }
        dups.each{ |k,v| code(k.to_file, v...) }
    }

    return()
}

var duplicates = Hash()
func collect(*files) {
    duplicates{files[0].size} := [] << files
}

find_duplicate_files(collect, Num(ARGV.shift), ARGV...)

for k,v in (duplicates.sort_by { |k| -k.to_i }) {
    say "=> Size: #{k}\n#{'~'*80}"
    for files in v {
        say "#{files.sort.join(%Q[\n])}\n#{'-'*80}"
    }
}
```


Section of sample output:


#### Output:
```
% sidef fdf.sf 0 /tmp /usr/bin
=> Size: 5656
~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/bin/precat
/usr/bin/preunzip
/usr/bin/prezip
--------------------------
=> Size: 2305
~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/bin/gunzip
/usr/bin/uncompress
--------------------------
=> Size: 2
~~~~~~~~~~~~~~~~~~~~~~~~~~
/tmp/a.txt
/tmp/b.txt
--------------------------
/tmp/m.txt
/tmp/n.txt
--------------------------
```
