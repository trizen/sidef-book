[1]: https://rosettacode.org/wiki/Include_a_file

# [Include a file][1]

Include a file in the current namespace:

```ruby
include('file.sf')
```


Include a file as module (file must exists in `SIDEF_INC` as `Some/Name.sm`):

```ruby
include Some::Name
# variables are available here as: Some::Name::var_name
```
