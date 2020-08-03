# Date

The Date class provides support for working with dates.

```ruby
var d1 = Date() # localtime date

say d1.day  #=> 5
say d1.mon  #=> 2
say d1.year #=> 2020

# Parse date
var d2 = Date.parse("2020-02-02", "%Y-%m-%d")

say (d1 - d2)       # difference in seconds
say (d1 <=> d2)     # date comparison

say d1.add_days(3)      # add n days
say d1.add_months(5)    # add n months
say d1.add_years(9)     # add n years

say (d1 == d2)      # check equality
say (d1 != d2)      # check inequality

say d1.epoch        # seconds since the epoch

# Format
say Time().local.format("%Y-%m-%d")        # current date

# Validate date
say Date.valid("2020-06-30", "%Y-%m-%d")    #=> true
say Date.valid("2020-06-31", "%Y-%m-%d")    #=> false
```
