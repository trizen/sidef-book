# Deparsing

Deparsing is the reverse process of parsing, which translates the AST back into code. Currently, Sidef supports deparsing into two languages with the `-R lang` command-line switch:

* `-R perl`
    - Deparses the AST into valid Perl code.
* `-R sidef`
    - Deparses the AST into valid Sidef code.

Example:

```shell
$ sidef -Rperl script.sf | perl
```

The `-Rsidef` switch (or simply `-r`) it's very useful to check how the parser really parses the code.

Example:
```shell
$ sidef -r -E 'sqrt(42)'
```

Outputs:
```ruby
42->sqrt;
```

Alternatively, Sidef can deparse code in interactive mode as well:

```shell
$ sf -i -Rperl
>>> [1,2,3]

use constant {
    Number177381361 => Sidef::Types::Number::Number->new('1'),
    Number176118801 => Sidef::Types::Number::Number->new('2'),
    Number175894561 => Sidef::Types::Number::Number->new('3'),
};

Sidef::Types::Array::Array->new((main::Number177381361), (main::Number176118801), (main::Number175894561));
```
