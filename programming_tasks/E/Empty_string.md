[1]: http://rosettacode.org/wiki/Empty_string

# [Empty string][1]

Create an empty string:

```ruby
s = "";
s = String.new;
```


These expressions all evaluate to true to determine emptiness:

```ruby
s == "";
s.length == 0;
s.is_empty;
s ~~ /^\z/;
s ~~ /\A\z/;
```


Non-empty expressions, in addition to simply negating the above expressions:

```ruby
s != "";
s.length?;
s.length > 0;
s ~~ /./s;
s !~ /^\z/;
```
