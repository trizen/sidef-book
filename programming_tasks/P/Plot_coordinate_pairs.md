[1]: https://rosettacode.org/wiki/Plot_coordinate_pairs

# [Plot coordinate pairs][1]

```ruby
require('GD::Graph::points')

var data = [
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    [2.7, 2.8, 31.4, 38.1, 58.0, 76.2, 100.5, 130.0, 149.3, 180.0],
]

var graph = %s'GD::Graph::points'.new(400, 300)
var gd = graph.plot(data)

var format = 'png'
File("qsort-range.#{format}").write(gd.(format), :raw)
```
