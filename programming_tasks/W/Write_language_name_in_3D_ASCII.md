[1]: http://rosettacode.org/wiki/Write_language_name_in_3D_ASCII

# [Write language name in 3D ASCII][1]

```ruby
var text = <<'EOT';
 
     ***
    *     *     *        **
    *           *       *
    *     *     *  ***  **
     ***  *  **** *   * *
        * * *   * ***** *
        * * *   * *     *
        * * *   * *     *
     ***  *  ****  ***  *
 
EOT
 
func banner3D(text, shift=-1) {
    var txt = text.lines.map{|line| line.gsub('*','__/').gsub(' ','   ')};
    var offset = txt.len.of {|i| " " * (shift.abs * i)};
    shift < 0 && offset.reverse!;
    (offset »+« txt).join("\n");
};
 
say banner3D(text);
```

#### Output:
```
          
                        __/__/__/
                    __/               __/               __/                        __/__/
                   __/                                 __/                     __/
                  __/               __/               __/      __/__/__/      __/__/
                    __/__/__/      __/      __/__/__/__/   __/         __/   __/
                            __/   __/   __/         __/   __/__/__/__/__/   __/
                           __/   __/   __/         __/   __/               __/
                          __/   __/   __/         __/   __/               __/
                __/__/__/      __/      __/__/__/__/      __/__/__/      __/
            
```