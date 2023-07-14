[1]: https://rosettacode.org/wiki/Search_a_list_of_records

# [Search a list of records][1]

```ruby
struct City {
    String name,
    Number population,
}
 
var cities = [
    City("Lagos", 21),
    City("Cairo", 15.2),
    City("Kinshasa-Brazzaville", 11.3),
    City("Greater Johannesburg", 7.55),
    City("Mogadishu", 5.85),
    City("Khartoum-Omdurman", 4.98),
    City("Dar Es Salaam", 4.7),
    City("Alexandria", 4.58),
    City("Abidjan", 4.4),
    City("Casablanca", 3.98),
]
 
say cities.index{|city| city.name == "Dar Es Salaam"}   # => 6
say cities.first{|city| city.population < 5.0}.name     # => Khartoum-Omdurman
```