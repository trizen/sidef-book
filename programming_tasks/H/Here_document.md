[1]: https://rosettacode.org/wiki/Here_document

# [Here document][1]

There must not be a space between the "&lt;&lt;" and the token string.
When the token string is double-quoted ("") or not quoted,
the content will be interpolated like a double-quoted string:

```ruby
var text = <<"EOF"
a = #{1+2}
b = #{3+4}
EOF
```


If single quotes are used, then the here document will not support interpolation, like a normal single-quoted string:

```ruby
var x = <<'FOO'
No
#{interpolation}
here
FOO
```


The here document does not start immediately at the "&lt;&lt;END" token -- it starts on the next line. The "&lt;&lt;END" is actually an expression, whose value will be substituted by the contents of the here document.
To further illustrate this fact, we can use the "&lt;&lt;END" inside a complex, nested expression:

```ruby
say (<<EOF + "lamb")
Mary had
  a little
EOF
```


which is equivalent with:

```ruby
say (<<EOF
Mary had
  a little
EOF
+ "lamb");
```
