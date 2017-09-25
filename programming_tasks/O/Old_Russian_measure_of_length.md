[1]: https://rosettacode.org/wiki/Old_Russian_measure_of_length

# [Old Russian measure of length][1]

```ruby
func convert (magnitude, unit) {
     var factor = Hash(
        tochka     => 0.000254,
        liniya     => 0.00254,
        diuym      => 0.0254,
        vershok    => 0.04445,
        piad       => 0.1778,
        fut        => 0.3048,
        arshin     => 0.7112,
        sazhen     => 2.1336,
        versta     => 1066.8,
        milia      => 7467.6,
        centimeter => 0.01,
        meter      => 1,
        kilometer  => 1000,
    )
 
    var meters = (magnitude * factor{unit.lc})
    say("#{magnitude} #{unit} to:\n", '-' * 40)
 
    for u,f in (factor.sort_by { |_,v| v }) {
        printf("%10s: %s\n", u, meters / f) if (u != unit.lc)
    }
}
 
convert(1, 'meter')
say('')
convert(1, 'milia')
```

#### Output:
```
1 meter to:
----------------------------------------
    tochka: 3937.007874015748031496062992125984251968503937007874
    liniya: 393.700787401574803149606299212598425196850393700787
centimeter: 100
     diuym: 39.370078740157480314960629921259842519685039370079
   vershok: 22.497187851518560179977502812148481439820022497188
      piad: 5.624296962879640044994375703037120359955005624297
       fut: 3.28083989501312335958005249343832020997375328084
    arshin: 1.406074240719910011248593925759280089988751406074
    sazhen: 0.468691413573303337082864641919760029996250468691
 kilometer: 0.001
    versta: 0.000937382827146606674165729283839520059992500937
     milia: 0.000133911832449515239166532754834217151427500134

1 milia to:
----------------------------------------
    tochka: 29400000
    liniya: 2940000
centimeter: 746760
     diuym: 294000
   vershok: 168000
      piad: 42000
       fut: 24500
    arshin: 10500
     meter: 7467.6
    sazhen: 3500
 kilometer: 7.4676
    versta: 7
```