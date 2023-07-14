[1]: https://rosettacode.org/wiki/Separate_the_house_number_from_the_street_name

# [Separate the house number from the street name][1]

```ruby
var re = %r[
    ( .*? )
    (?:
        \s+
        (
        | \d+ (?: \- | \/ ) \d+
        | (?! 1940 | 1945) \d+ [ a-z I . / \x20 ]* \d*
        )
    )?
$]x
 
ARGF.each { |line|
    line.chomp!
    if (var m = line.match(re)) {
        printf("%-25s split as (#{m[0]}, #{m[1]})\n", line)
    }
    else {
        warn "Can't parse: «#{line}»"
    }
}
```

#### Output:
```
Plataanstraat 5           split as (Plataanstraat, 5)
Straat 12                 split as (Straat, 12)
Straat 12 II              split as (Straat, 12 II)
Dr. J. Straat   12        split as (Dr. J. Straat, 12)
Dr. J. Straat 12 a        split as (Dr. J. Straat, 12 a)
Dr. J. Straat 12-14       split as (Dr. J. Straat, 12-14)
Laan 1940 – 1945 37       split as (Laan 1940 – 1945, 37)
Plein 1940 2              split as (Plein 1940, 2)
1213-laan 11              split as (1213-laan, 11)
16 april 1944 Pad 1       split as (16 april 1944 Pad, 1)
1e Kruisweg 36            split as (1e Kruisweg, 36)
Laan 1940-’45 66          split as (Laan 1940-’45, 66)
Laan ’40-’45              split as (Laan ’40-’45, )
Langeloërduinen 3 46      split as (Langeloërduinen, 3 46)
Marienwaerdt 2e Dreef 2   split as (Marienwaerdt 2e Dreef, 2)
Provincialeweg N205 1     split as (Provincialeweg N205, 1)
Rivium 2e Straat 59.      split as (Rivium 2e Straat, 59.)
Nieuwe gracht 20rd        split as (Nieuwe gracht, 20rd)
Nieuwe gracht 20rd 2      split as (Nieuwe gracht, 20rd 2)
Nieuwe gracht 20zw /2     split as (Nieuwe gracht, 20zw /2)
Nieuwe gracht 20zw/3      split as (Nieuwe gracht, 20zw/3)
Nieuwe gracht 20 zw/4     split as (Nieuwe gracht, 20 zw/4)
Bahnhofstr. 4             split as (Bahnhofstr., 4)
Wertstr. 10               split as (Wertstr., 10)
Lindenhof 1               split as (Lindenhof, 1)
Nordesch 20               split as (Nordesch, 20)
Weilstr. 6                split as (Weilstr., 6)
Harthauer Weg 2           split as (Harthauer Weg, 2)
Mainaustr. 49             split as (Mainaustr., 49)
August-Horch-Str. 3       split as (August-Horch-Str., 3)
Marktplatz 31             split as (Marktplatz, 31)
Schmidener Weg 3          split as (Schmidener Weg, 3)
Karl-Weysser-Str. 6       split as (Karl-Weysser-Str., 6)
```