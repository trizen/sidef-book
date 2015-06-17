[1]: http://rosettacode.org/wiki/JSON

# [JSON][1]

```ruby
var json = require('JSON').new;
var data = json.decode('{"blue": [1, 2], "ocean": "water"}');
say data.dump;
data[:ocean] = Hash.new(water => %w[fishy salty]);
say json.encode(data);
```

#### Output:
```
Hash.new(
    'blue' => [1, 2],
    'ocean' => 'water'
    )
{"blue":[1,2],"ocean":{"water":["fishy","salty"]}}
```