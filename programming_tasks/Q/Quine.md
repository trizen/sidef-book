[1]: http://rosettacode.org/wiki/Quine

# [Quine][1]

With printf():

```ruby
s = %(s = %%(%s); printf(s, s);
); printf(s, s);
```


With HERE-doc:

```ruby
say(<<e*2, 'e')
say(<<e*2, 'e')
e
```