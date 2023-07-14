[1]: https://rosettacode.org/wiki/Calendar_-_for_"REAL"_programmers

# [Calendar - for &quot;REAL&quot; programmers][1]

```ruby
-> DT { ('DATE'.("\LWC") + 'TIME'.("\LWC")).("\LREQUIRE") }

-> MONTHS_PER_COL { 6 }
-> WEEK_DAY_NAMES { <MO TU WE TH FR SA SU> }
-> MONTH_NAMES    { <JAN FEB MAR APR MAY JUN JUL AUG SEP OCT NOV DEC> }

-> FMT_MONTH (YEAR, MONTH, STR="", WEEK_DAY=0) {
    STR  = "%11\LS\E%9\LS\E\12".("\LSPRINTF")(MONTH_NAMES()[MONTH-1],'')
    STR += (WEEK_DAY_NAMES().("\LJOIN")(' ') + "\12")

    -> DATE { DT().("\LNEW")("\LYEAR" => YEAR, "\LMONTH" => MONTH) }

    WEEK_DAY = DATE().("\LDAY_OF_WEEK")
    STR += (["  "] * WEEK_DAY-1 -> ("\LJOIN")(" "))

    -> LAST_DAY {
        DT().("\LLAST_DAY_OF_MONTH")(
            "\LYEAR" => YEAR, "\LMONTH" => MONTH
        ).("\LDAY")
    }

    (DATE().("\LDAY") .. LAST_DAY()).("\LEACH")({ |DAY|
        (WEEK_DAY ~~ (2..7)) && (STR += " ")

        (WEEK_DAY == 8) && (
            STR += "\12"
            WEEK_DAY = 1
        )
        STR += ("%2\LD" % DAY)
        ++WEEK_DAY
    })
    (WEEK_DAY < 8) && (STR += " ")
    STR += (["  "] * 8-WEEK_DAY -> ("\LJOIN")(" "))
    STR += "\12"
}

-> FMT_YEAR (YEAR, STR="", MONTH_STRS=[]) {
    MONTH_STRS = 12.("\LOF")({|I| FMT_MONTH(YEAR, I+1).("\LLINES") })

    STR += (' '*(MONTHS_PER_COL()*10 + 2) + YEAR + "\12")
    (0..11 -> ("\LBY")(MONTHS_PER_COL())).("\LEACH")({ |MONTH|
        MONTH_STRS[MONTH] && ->() {
            { |I|
                MONTH_STRS[MONTH + I] && (
                    STR += MONTH_STRS[MONTH + I].("\LSHIFT")
                    STR += ' '*2
                )
            } * MONTHS_PER_COL()

            STR += "\12"
            MONTH_STRS[MONTH] && __FUNC__()
        }()
        STR += "\12"
    })

    STR
}

FMT_YEAR(ARGV ? ARGV[0].("\LTO_I") : 1969).("\LPRINT")
```

#### Output:
```
                                                              1969
        JAN                   FEB                   MAR                   APR                   MAY                   JUN
MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU
       1  2  3  4  5                  1  2                  1  2      1  2  3  4  5  6            1  2  3  4                     1
 6  7  8  9 10 11 12   3  4  5  6  7  8  9   3  4  5  6  7  8  9   7  8  9 10 11 12 13   5  6  7  8  9 10 11   2  3  4  5  6  7  8
13 14 15 16 17 18 19  10 11 12 13 14 15 16  10 11 12 13 14 15 16  14 15 16 17 18 19 20  12 13 14 15 16 17 18   9 10 11 12 13 14 15
20 21 22 23 24 25 26  17 18 19 20 21 22 23  17 18 19 20 21 22 23  21 22 23 24 25 26 27  19 20 21 22 23 24 25  16 17 18 19 20 21 22
27 28 29 30 31        24 25 26 27 28        24 25 26 27 28 29 30  28 29 30              26 27 28 29 30 31     23 24 25 26 27 28 29

        JUL                   AUG                   SEP                   OCT                   NOV                   DEC
MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU  MO TU WE TH FR SA SU
    1  2  3  4  5  6               1  2  3   1  2  3  4  5  6  7         1  2  3  4  5                  1  2   1  2  3  4  5  6  7
 7  8  9 10 11 12 13   4  5  6  7  8  9 10   8  9 10 11 12 13 14   6  7  8  9 10 11 12   3  4  5  6  7  8  9   8  9 10 11 12 13 14
14 15 16 17 18 19 20  11 12 13 14 15 16 17  15 16 17 18 19 20 21  13 14 15 16 17 18 19  10 11 12 13 14 15 16  15 16 17 18 19 20 21
21 22 23 24 25 26 27  18 19 20 21 22 23 24  22 23 24 25 26 27 28  20 21 22 23 24 25 26  17 18 19 20 21 22 23  22 23 24 25 26 27 28
28 29 30 31           25 26 27 28 29 30 31  29 30                 27 28 29 30 31        24 25 26 27 28 29 30  29 30 31
```
