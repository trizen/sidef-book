[1]: http://rosettacode.org/wiki/Find_duplicate_files

# [Find duplicate files][1]

It uses the portable _File::Find_ module which means that it should work, virtually, on any platform.

```ruby
# usage: sidef fdf.sf [size] [dir1] [...]

func find_duplicate_files(Block code, size_min=0, *dirs) {
    var files = Hash()
    var f = frequire('File::Find')
    f.find(
        Hash(
            no_chdir => true,
            wanted   => func(arg) {
                var file = File(arg)
                file.is_file || return nil;
                file.is_link && return nil;
                var size = file.size
                size >= size_min || return nil;
                files{size} := [] << file
            },
        ) => dirs...
    )

    files.values.each { |set|
        set.len > 1 || next
        var dups = Hash()
        for i in (0 ..^ set.end-1) {
            for (var j = i+1; j <= set.end; j++) {
                if (set[i].compare(set[j]) == 0) {
                    dups{set[i]} := [] << set.pop_at(j--)
                }
            }
        }
        dups.each{ |k,v| code(k.to_file, v...) }
    }

    return nil;
}

var duplicates = Hash()
func collect(*files) {
    duplicates{files[0].size} := [] << files
}

find_duplicate_files(collect, Num(ARGV.shift), ARGV...)

duplicates.keys.sort_by{ .to_i }.reverse.each { |key|
    say "=> Size: #{key}\n#{'~'*80}"
    duplicates{key}.each { |files|
        say "#{files.map{.to_s}.sort.join(%Q[\n])}\n#{'-'*80}"
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
