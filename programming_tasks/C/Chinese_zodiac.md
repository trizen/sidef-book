[1]: https://rosettacode.org/wiki/Chinese_zodiac

# [Chinese zodiac][1]

```ruby
func zodiac(year) {
  var animals = %w(Rat Ox Tiger Rabbit Dragon Snake Horse Goat Monkey Rooster Dog Pig)
  var elements = %w(Wood Fire Earth Metal Water)
  var terrestrial_han = %w(子 丑 寅 卯 辰 巳 午 未 申 酉 戌 亥)
  var terrestrial_pinyin = %w(zĭ chŏu yín măo chén sì wŭ wèi shēn yŏu xū hài)
  var celestial_han = %w(甲 乙 丙 丁 戊 己 庚 辛 壬 癸)
  var celestial_pinyin = %w(jiă yĭ bĭng dīng wù jĭ gēng xīn rén gŭi)
  var aspect = %w(yang yin)
 
  var cycle_year = ((year-4) % 60)
  var (i2, i10, i12) = (cycle_year%2, cycle_year%10, cycle_year%12)
 
  (year,
   celestial_han[i10],    terrestrial_han[i12],
   celestial_pinyin[i10], terrestrial_pinyin[i12],
   elements[i10 >> 1], animals[i12], aspect[i2], cycle_year+1)
}
 
[1935, 1938, 1968, 1972, 1976, 2017].each { |year|
    printf("%4d: %s%s (%s-%s) %s %s; %s - year %d of the cycle\n", zodiac(year))
}
```

#### Output:
```
1935: 乙亥 (yĭ-hài) Wood Pig; yin - year 12 of the cycle
1938: 戊寅 (wù-yín) Earth Tiger; yang - year 15 of the cycle
1968: 戊申 (wù-shēn) Earth Monkey; yang - year 45 of the cycle
1972: 壬子 (rén-zĭ) Water Rat; yang - year 49 of the cycle
1976: 丙辰 (bĭng-chén) Fire Dragon; yang - year 53 of the cycle
2017: 丁酉 (dīng-yŏu) Fire Rooster; yin - year 34 of the cycle
```