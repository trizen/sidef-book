# String

A String represents an immutable sequence of UTF-8 characters.

## Double quoted strings


A String is typically created with a string literal, enclosing UTF-8 characters in double quotes:

```ruby
"hello world"
```


Being a new programming language, Sidef has built-in support for Unicode quotes as well:

```ruby
„double\tquoted”        # == "double    quoted"
```

A backslash can be used to denote some characters inside the string:

```ruby
"\""    # double quote
"\\"    # backslash
"\e"    # escape
"\f"    # form feed
"\n"    # newline
"\r"    # carriage return
"\t"    # tab
"\s"    # space
"\v"    # vertical tab
```


You can use `\o{...}` to denote a code point written in octal:

```ruby
"\o{101}"   # == "A"
"\o{123}"   # == "S"
"\o{12}"    # == "\n"
"\o{1}"     # string with one character with code point 1
```


Or you can use `\x{...}` and specify hexadecimal numbers:

```ruby
"\x{41}"    # == "A"
"\x{263a}"  # == "☺"
```


To specity Unicode names, you can use `\N{...}`:

```ruby
"\N{WHITE SMILING FACE}"            # == "☺"
"\N{GREEK CAPITAL LETTER GAMMA}"    # == "Γ"
```


A string can span multiple lines:

```ruby
"hello
world"    # same as "hello\nworld"
```


If you need to write a string that has many double quotes, parenthesis, or similar characters, you can use alternative literals:

```ruby
# Supports double quotes and nested parenthesis
%(hello ("world"))  # same as "hello (\"world\")"

# Supports double quotes and nested brackets
%[hello ["world"]]  # same as "hello [\"world\"]"

# Supports double quotes and nested curlies
%{hello {"world"}}  # same as "hello {\"world\"}"

# Supports double quotes and nested angles
%<hello <"world">>  # same as "hello <\"world\">"
```


The Parser is aware of Unicode delimiters as well. Here are only a few examples:

```ruby
%„...”
%«...»
%⦑...⦒
%「...」
```


### Interpolation

To create a String with embedded expressions, you can use string interpolation:

```ruby
"sum = #{1 + 2}"        # "sum = 3"
```

## Single quoted strings

Single quoted strings does not support escapes, nor interpolation.

```ruby
'single\tquoted'   # creates a string as it is
```

To specify a custom delimiter, you can use `%q` followed by any non-whitespace delimiter:

```ruby
%q(hello ('world'))     # same as 'hello (\'world\')'
```

Another way of writing string literals, is by placing a colon in font of an alphanumeric string that begins with a letter.

```ruby
:word          # == 'word'
:another_word  # == 'another_word'
```

## Here-document

There must not be a space between the `<<` and the token string.
When the token string is double-quoted (`""`) or not quoted,
the content will be interpolated like a double-quoted string:

```ruby
<<"EOF";
a = #{1+2}
b = #{3+4}
EOF
```


If single quotes are used, then the here document will not support interpolation, like a normal single-quoted string:

```ruby
<<'FOO';
No
#{interpolation}
here
FOO
```


The here document does not start immediately at the `<<END` token -- it starts on the next line. The `<<END` is actually an expression, whose value will be substituted by the contents of the here document.
To further illustrate this fact, we can use the `<<END` inside a complex, nested expression:

```ruby
(<<EOF + "lamb");
Mary had
  a little
EOF
```


which is equivalent with:

```ruby
(<<EOF
Mary had
  a little
EOF
+ "lamb");
```
