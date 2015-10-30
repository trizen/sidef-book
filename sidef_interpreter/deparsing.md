# Deparsing

The deparsing is the reverse process of parsing, which translates the AST back into code.

Currently, Sidef supports deparsing into two languages with the `-R` switch:

* -Rperl
    Parses and deparses the AST into valid Perl code.
* -Rsidef
    Parses and deparses the AST into valid Sidef code.

Example:

```shell
$ sidef -Rperl script.sf | perl
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
