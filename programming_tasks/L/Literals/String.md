[1]: http://rosettacode.org/wiki/Literals/String

# [Literals/String][1]

Quotes that do not interpolate:

```ruby
'single quotes with \'embedded quote\' and \\backslash';
‚unicode single quoted’;
%q(not interpolating with (nested) parentheses
and newline);
```


Quotes that interpolate:

```ruby
var a = 42;
"double \Uquotes\E with \"embedded quote\"\nnewline and variable interpolation: #{a} % 10 = #{a % 10}";
„same as above”;
%Q(same as above);
```


Heredocs:

```ruby
print <<EOT
Implicit double-quoted (interpolates):
a = #{a}
EOT
 
print <<"EOD"
Explicit double-quoted with interpolation:
a = #{a}
EOD
 
print <<'NON_INTERPOLATING'
This will not interpolate: #{a}
NON_INTERPOLATING
```