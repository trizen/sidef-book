[1]: https://rosettacode.org/wiki/Names_to_numbers

# [Names to numbers][1]

```ruby
func names_to_number(str) {
 
    static nums = Hash.new(
           zero => 0,             one => 1,             two => 2,
          three => 3,            four => 4,            five => 5,
            six => 6,           seven => 7,           eight => 8,
           nine => 9,             ten => 10,         eleven => 11,
         twelve => 12,       thirteen => 13,       fourteen => 14,
        fifteen => 15,        sixteen => 16,      seventeen => 17,
       eighteen => 18,       nineteen => 19,         twenty => 20,
         thirty => 30,          forty => 40,          fifty => 50,
          sixty => 60,        seventy => 70,         eighty => 80,
         ninety => 90,        hundred => 1e2,      thousand => 1e3,
        million => 1e6,       billion => 1e9,      trillion => 1e12,
    quadrillion => 1e15,  quintillion => 1e18,
    );
 
    # Groupings for thousands, millions, ..., quintillions
    static groups = /\d{4}|\d{7}|\d{10}|\d{13}|\d{16}|\d{19}/;
 
    # Numeral
    static num = /\d+/;
 
    str.trim!;                      # remove leading and trailing whitespace
    str.gsub!('-', ' ');            # convert hyphens to spaces
    str.words!.join!(' ');          # remove duplicate whitespace, convert ws to space
    str.lc!;                        # convert to lower case
 
    # tokenize sentence boundaries
    str.gsub!(/([.?!]) /, {|a| ' ' + a + "\n"});
    str.gsub!(/([.?!])$/, {|a| ' ' + a + "\n"});
 
    # tokenize other punctuation and symbols
    str.gsub!(/\$(.)/,           {|a| "$ #{a}" });       # prefix
    str.gsub!(/(.)([;:%'',])/, {|a,b| "#{a} #{b}"});     # suffix
 
    nums.each { |key, value| str.gsub!(Regex.new('\b' + key + '\b'), value) };
 
    str.gsub!(/(\d) , (\d)/,   {|a,b| a + ' ' + b});
    str.gsub!(/(\d) and (\d)/, {|a,b| a + ' ' + b});
 
    static regex = [
        Regex.new('\b(\d) 100 (\d\d) (\d) (' + groups + ')\b'),
        Regex.new('\b(\d) 100 (\d\d) (' + groups + ')\b'),
        Regex.new('\b(\d) 100 (\d) (' + groups + ')\b'),
        Regex.new('\b(\d) 100 (' + groups + ')\b'),
        Regex.new('\b100 (\d\d) (\d) (' + groups + ')\b'),
        Regex.new('\b100 (\d\d) (' + groups + ')\b'),
        Regex.new('\b100 (\d) (' + groups + ')\b'),
        Regex.new('\b100 (' + groups + ')\b'),
        Regex.new('\b(\d\d) (\d) (' + groups + ')\b'),
        Regex.new('\b(\d{1,2}) (' + groups + ')\b'),
        Regex.new('((?:' + num + ' )*' + num + ')'),
    ];
 
    str.gsub!(regex[0], {|a,b,c,d| (a.to_i*100 + b.to_i + c.to_i) * d.to_i });
    str.gsub!(regex[1], {|a,b,c|   (a.to_i*100 + b.to_i) * c.to_i });
    str.gsub!(regex[2], {|a,b,c|   (a.to_i*100 + b.to_i) * c.to_i });
    str.gsub!(regex[3], {|a,b|     (a.to_i * b.to_i * 100) });
    str.gsub!(regex[4], {|a,b,c|   (100 + a.to_i + b.to_i) * c.to_i });
    str.gsub!(regex[5], {|a,b|     (100 + a.to_i) * b.to_i });
    str.gsub!(regex[6], {|a,b|     (100 + a.to_i) * b.to_i });
    str.gsub!(regex[7], {|a|       (a.to_i * 100) });
    str.gsub!(regex[8], {|a,b,c|   (a.to_i + b.to_i) * c.to_i });
    str.gsub!(regex[9], {|a,b|     (a.to_i * b.to_i) });
 
    str.gsub!(/\b(\d\d) (\d) 100\b/, {|a,b| (a.to_i + b.to_i) * 100});
    str.gsub!(/\b(\d{1,2}) 100\b/,   {|a|   (a.to_i * 100) });
    str.gsub!(/\b(\d{2}) (\d{2})\b/, {|a,b| (a.to_i * 100) + b.to_i});
    str.gsub!(regex[10], {|a| a.split(' ').map{.to_i}.sum });
}
```


Usage:

```ruby
ARGF.each { |line|
    say "#{line.chomp.dump} --> #{names_to_number(line).dump}";
}
```


Sample:


#### Output:
```
$ sidef names2nums.sf input.txt
"Seventy two dollars" --> "72 dollars"
"One Hundred and One Dalmatians" --> "101 dalmatians"
"Two Thousand and One: A Space Odyssey" --> "2001 : a space odyssey"
"Twenty Thirteen" --> "2013"
"Nineteen Eighty-Four" --> "1984"
"one thousand, five hundred and one" --> "1501"
"three hundred and ten" --> "310"
"ninety-nine" --> "99"
"ninety nine thousand nine hundred ninety nine" --> "99999"
"five hundred and twelve thousand, six hundred and nine" --> "512609"
"two billion, one hundred" --> "2000000100"
```