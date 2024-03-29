[1]: https://rosettacode.org/wiki/IBAN

# [IBAN][1]

```ruby
func valid_iban(iban) {
  static len = Hash(
    AD=>24, AE=>23, AL=>28, AO=>25, AT=>20, AZ=>28, BA=>20, BE=>16, BF=>27,
    BG=>22, BH=>22, BI=>16, BJ=>28, BR=>29, CG=>27, CH=>21, CI=>28, CM=>27,
    CR=>21, CV=>25, CY=>28, CZ=>24, DE=>22, DK=>18, DO=>28, DZ=>24, EE=>20,
    EG=>27, ES=>24, FI=>18, FO=>18, FR=>27, GA=>27, GB=>22, GE=>22, GI=>23,
    GL=>18, GR=>27, GT=>28, HR=>21, HU=>28, IE=>22, IL=>23, IR=>26, IS=>26,
    IT=>27, JO=>30, KW=>30, KZ=>20, LB=>28, LI=>21, LT=>20, LU=>20, LV=>21,
    MC=>27, MD=>24, ME=>22, MG=>27, MK=>19, ML=>28, MR=>27, MT=>31, MU=>30,
    MZ=>25, NL=>18, NO=>15, PK=>24, PL=>28, PS=>29, PT=>25, QA=>29, RO=>24,
    RS=>22, SA=>24, SE=>24, SI=>19, SK=>24, SM=>27, SN=>28, TN=>24, TR=>26,
    UA=>29, VG=>24,
  )
 
  # Ensure upper alphanumeric input.
  iban -= /\s+/g
  iban.uc! ~~ /^[0-9A-Z]+\z/ || return false
 
  # Validate country code against expected length.
  var cc = iban.substr(0, 2)
  iban.len == len{cc} || return false
 
  # Shift and convert.
  iban.sub!(/(.{4})(.+)/, {|a,b| b+a})
  iban.gsub!(/([A-Z])/,   {|a| a.ord - 55})
 
  iban.to_i % 97 == 1
}
 
say valid_iban("GB82 WEST 1234 5698 7654 32") #=> true
say valid_iban("GB82 TEST 1234 5698 7654 32") #=> false
```
