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

The `-Rsidef` switch (or simply `-r`) is useful for verifying how the code is parsed.

Example:
```shell
$ sidef -r -E '1 + 2/3'
```

Outputs:
```ruby
(1)->+((2)->/(3));
```

Deparsing can also be enabled in interactive mode:

```shell
$ sidef -i -r
Sidef 3.05 on linux
Type "help", "copyright" or "license" for more information.
>> [1,2,3].map { .sqrt }
[1, 2, 3]->map({|_| (_->sqrt()) });
>>
```
